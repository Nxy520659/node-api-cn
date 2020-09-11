<!-- YAML
added: v12.0.0
-->

* `port` {integer}
* `address` {string}
* `callback` {Function} 当连接完成或出错时调用。

为 `dgram.Socket` 关联一个远程地址和端口。
这个 socket 句柄发送的任何消息都会被发送到关联的远程地址。
而且，这个套接字会只接受来自那个远程同类的消息。
尝试在已连接的套接字上调用connect（）将导致 [`ERR_SOCKET_DGRAM_IS_CONNECTED`][] 异常。
如果没有提供 `address`，会默认用 `'127.0.0.1'`（适用于 `udp4` 套接字）或者 `'::1'`（适用于 `udp6` 套接字）。
一旦连接完成，一个 `'connect'` 会触发，并且可选的 `callback` 也会被调用。
发生失败时，这个 `callback` 被调用或者触发一个 `'error'` 事件。
