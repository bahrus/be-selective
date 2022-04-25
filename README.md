# be-selective

be-selective has a most unhappy job.  Its role is extremely limited, and all it does is act as a gatekeeper.  And its days may be numbered, as it wouldn't serve much of a purpose if https://github.com/WICG/webcomponents/issues/809 is ever addressed.

be-selective works in conjunction with be-born.

```html
<my-web-component be-selective>
    
    #shadowroot
    ...
        <template be-born><template>
</my-web-component>

```

be-selective searches inside the shadow root for all template elements with the attribute be-born, and instantiates them as "light" elements.

If the attribute of be-born is "as-is", then the template is simply copied as is as a "light element."  Otherwise the template is cloned and appended.

If be-selective has a value, then it is used as a "matches" criteria on the template elements with attribute be-born.

be-born, on the other hand, looks at the containing host, for attribute be-selective/is-selective.  If it exists, be-born does nothing.

If it isn't there, be-born instantiates itself into the host's light children.