# cv-memory-leak

When trying to store `new cv.Mat()` instances the memory fills up but garbage collector does not pick up the deleted objects.

Mat instances have a `.delete()` method that removes the matrix, however browser runtimes don't pick that up.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

## Steps to reproduce

1. Open browser after serving the project
2. Open task manager (chrome) and view the used memory of you application
3. Click on the "create frames" button which will create new cv.Mat objects and store them into array.
4. Check for increased memory footprint on the task manager
5. Click "delete frames" button to clear out the frames.
6. Check if the used memory decreased.
    (hint: it does not decrease as garbage collector fails at this.)