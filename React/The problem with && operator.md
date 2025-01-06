**Do not** use 0 as falsy in the [[The && operator|&&]] case, like this:
`{unreadMessages.length && <p>{unreadMessages.length} unread messages!</p>}`

You must instead do this.
`{unreadMessages.length > 0 && <p>{unreadMessages.length} unread messages!</p>}`

Because otherwise it will render '0' and not nothing (false) to the screen as explained in [[The && operator]]
