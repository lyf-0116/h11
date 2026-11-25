Strip ``Content-Length``, ``Transfer-Encoding``, and ``Trailer`` headers from
outgoing bodyless responses, so that the framing headers cannot contradict the
empty body. Pass ``strip_bodyless_response_headers=False`` to :class:`Connection`
to preserve the previous behavior for compatibility.
