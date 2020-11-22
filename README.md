# react-google-translate

> Useful hook for Google Translate API.

[![NPM](https://img.shields.io/npm/v/react-google-translate.svg)](https://www.npmjs.com/package/react-google-translate) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Install

```bash
npm install --save react-google-translate @google-cloud/translate
```

## Usage

```tsx
import React, { useState, useEffect } from 'react'

import { useLazyTranslate } from 'react-google-translate'

const Example = () => {

  const [text] = useState('test');
  const [language] = useState('zh-CN');

  const [translate, { data, loading }] = useLazyTranslate({
    language
  })

  useEffect(() => {
    if (text) {
      translate(text, language);
    }
  }, [translate, text])

  render() {
    return (
      <div>{loading ? 'Loading...' : data}</div>
    )
  }
}
```

## Props

### `language`: string | string[]

Set the default language for the translation.

## Environment variables

Generate your credentials and project id in Google Cloud Platform. Read through the [documentation](https://cloud.google.com/iam/docs/creating-managing-service-accounts) for setting a service account.

After you acquired your credentials and project id, add it to your environment variables.

```
GCP_PRIVATE_KEY=[private_key]
GCP_CLIENT_EMAIL=[client_email]
GCP_PROJECT_ID=[project_id]
```

## API

### `translate`: func

Calls the api to translate the given text and language.

### `loading`: boolean

Indicates that loading state.

### `data`: string | string[]

Translated text received from the hook.

### `called`: boolean

Indicates that hook has been triggered.

## License

MIT © [noahjohn9259](https://github.com/noahjohn9259)
