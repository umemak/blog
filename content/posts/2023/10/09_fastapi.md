---
title: "FastAPI入門"
date: "2023-10-09"
tags: ["FastAPI"]

---

[FastAPI入門](https://zenn.dev/sh0nk/books/537bb028709ab9)をやってみた。

特にひっかかることなく進めたが、最後のテストがPASSしない。

```sh
$ docker-compose run --entrypoint "poetry run pytest" demo-app
[+] Building 0.0s (0/0)                                                                                              docker:default 
[+] Building 0.0s (0/0)                                                                                              docker:default 
======================================================= test session starts ========================================================platform linux -- Python 3.9.17, pytest-7.4.2, pluggy-1.3.0
rootdir: /src
plugins: anyio-3.7.1, asyncio-0.21.1
asyncio: mode=strict
collected 2 items                                                                                                                   

tests/test_main.py FF                                                                                                        [100%]

============================================================= FAILURES =============================================================
_______________________________________________________ test_create_and_read _______________________________________________________

async_client = <async_generator object async_client at 0x7f8d3374dca0>

    @pytest.mark.asyncio
    async def test_create_and_read(async_client):
>       response = await async_client.post("/tasks", json={"title": "テストタスク"})
E       AttributeError: 'async_generator' object has no attribute 'post'

tests/test_main.py:41: AttributeError
__________________________________________________________ test_done_flag __________________________________________________________

async_client = <async_generator object async_client at 0x7f8d3374ddc0>

    @pytest.mark.asyncio
    async def test_done_flag(async_client):
>       response = await async_client.post("/tasks", json={"title": "テストタスク2"})
E       AttributeError: 'async_generator' object has no attribute 'post'

tests/test_main.py:56: AttributeError
========================================================= warnings summary =========================================================
.venv/lib/python3.9/site-packages/pydantic/fields.py:798
  /src/.venv/lib/python3.9/site-packages/pydantic/fields.py:798: PydanticDeprecatedSince20: Using extra keyword arguments on `Field` is deprecated and will be removed. Use `json_schema_extra` instead. (Extra keys: 'example'). Deprecated in Pydantic V2.0 to be removed in V3.0. See Pydantic V2 Migration Guide at https://errors.pydantic.dev/2.4/migration/
    warn(

.venv/lib/python3.9/site-packages/pydantic/_internal/_config.py:267
.venv/lib/python3.9/site-packages/pydantic/_internal/_config.py:267
.venv/lib/python3.9/site-packages/pydantic/_internal/_config.py:267
  /src/.venv/lib/python3.9/site-packages/pydantic/_internal/_config.py:267: PydanticDeprecatedSince20: Support for class-based `config` is deprecated, use ConfigDict instead. Deprecated in Pydantic V2.0 to be removed in V3.0. See Pydantic V2 Migration Guide at https://errors.pydantic.dev/2.4/migration/
    warnings.warn(DEPRECATION_MESSAGE, DeprecationWarning)

.venv/lib/python3.9/site-packages/pydantic/_internal/_config.py:317
  /src/.venv/lib/python3.9/site-packages/pydantic/_internal/_config.py:317: UserWarning: Valid config keys have changed in V2:
  * 'orm_mode' has been renamed to 'from_attributes'
    warnings.warn(message, UserWarning)

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
===================================================== short test summary info ======================================================
FAILED tests/test_main.py::test_create_and_read - AttributeError: 'async_generator' object has no attribute 'post'
FAILED tests/test_main.py::test_done_flag - AttributeError: 'async_generator' object has no attribute 'post'
================================================== 2 failed, 5 warnings in 29.49s ==================================================
```
