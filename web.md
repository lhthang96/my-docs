# DOCUMENTATION FOR WEB KNOWLEDGE

## Storages

**Ref**: https://viblo.asia/p/giua-local-storage-session-storage-va-cookie-co-gi-khac-biet-1VgZver2KAw?fbclid=IwAR0Y5fwI-8CARKUsKyssdAenLrTKKmA_TlxsJt2Vl3BZ2dPD-8zQxPFWuzE

### Local Storage

- Stored data will be stayed forever on browser until be deleted on `Application` tab on browser or by JavaScript `localStorage` API.

> **Note**: If user using `Incognito` tabs, `Local Storage` will be cleared after the last tab is closed.

- Capacity: 5MB
- Stored data won't be sent to `Server` by `request header`.
- Stored at the client side, `Local Storage` won't affect to apps performance, but to the browser (practically not significant).
- `Local storage` can be shared betweens tabs with a `same origin` (similarly have domain/port/protocol).

> **Note:** `Local Storage` could be accessed by JavaScript `localStorage` APIs -> Should not be used to store user sensitive data.

> **Note:** `Local Storage` APIs is synchronous.

### Session Storage

`Session Storage` is similar to `Local Storage`, there are only 2 different things:

- `Session Storage` is separated in each tab, meant even there are 2 tabs with a same domain, they still have different `Session Storage`.
- `Session Storage` will be cleared right after its tab is closed, but still be stayed if the tab is refreshed.

### Cookie

- Capacity: 4KB, `Chrome` and `Safari` supports unlimited cookies amount.
- Can be sent to server by `request header`.
- Having `expires` property to indicate valid time.

> **Tip:** Using `secure flag` to enhance security for cookie, it would be sent only when the connection is SSL.
