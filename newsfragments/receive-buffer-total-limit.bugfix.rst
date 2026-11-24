Add a ``max_event_buffer_size`` limit to ``Connection`` that caps the
total number of received-but-not-yet-consumed bytes held in the receive
buffer, including complete events queued up behind an incomplete one.
Previously only a single incomplete event was bounded
(``max_incomplete_event_size``), so a peer could make the buffer grow
without limit by sending many small, individually-complete events
faster than they were consumed. Exceeding the new limit causes
``receive_data`` to raise ``RemoteProtocolError``.
