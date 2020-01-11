# Uppy Spike for Prime Solo Project
Duration: 1 day

## Description 
This is a mini project to figure out and get comfortable using Uppy photo uploader in projects. I plan to incorporate Uppy into my Conscious Closet Solo Project. 

## How To Use Uppy
1. npm install @uppy/react
2. imports:
    > import React from 'react'

    > import Uppy from '@uppy/core'

    > import Tus from '@uppy/tus'

    > import { DragDrop } from '@uppy/react'
3. basic js
```javascript
const uppy = Uppy({
    meta: { type: 'avatar' },
    restrictions: { maxNumberOfFiles: 1 },
    autoProceed: true
  })
  
  uppy.use(Tus, { endpoint: '/upload' })
  
  uppy.on('complete', (result) => {
    const url = result.successful[0].uploadURL
    store.dispatch({
      type: 'SET_USER_AVATAR_URL',
      payload: { url: url }
    })
  })
  
  const AvatarPicker = ({ currentAvatar }) => {
    return (
      <div>
        <img src={currentAvatar} alt="Current Avatar" />
        <DragDrop
          uppy={uppy}
          locale={{
            strings: {
              // Text to show on the droppable area.
              // `%{browse}` is replaced with a link that opens the system file selection dialog.
              dropHereOr: 'Drop here or %{browse}',
              // Used as the label for the link that opens the system file selection dialog.
              browse: 'browse'
            }
          }}
        />
      </div>
    )
  }
```