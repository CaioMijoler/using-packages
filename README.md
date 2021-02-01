# using-packages

Gerando apk - pasta raiz projeto -> cd android; ./gradlew clean; ./gradlew assembleRelease;

pasta build -> nomePojeto\android\app\build\outputs\apk\release;

alterando img -> \android\app\ser\main\res\ 
        36 x 36 (0,75 x) para densidade baixa (ldpi)
        48 x 48 (configuração básica de 1,0 x) para densidade média (mdpi)
        72 x 72 (1,5 x) para densidade alta (hdpi)
        96 x 96 (2,0 x) para densidade extra-alta (xhdpi)
        144 x 144 (3,0 x) para densidade extra-extra-alta (xxhdpi)
        192 x 192 (4,0 x) para densidade extra-extra-extra-alta (xxxhdpi);



ANDROID APP REQUEST PERMISSIONS

import { PermissionsAndroid } from 'react-native';

const checkAllPermissions = async (): Promise<boolean | undefined> => {
    try {
      await PermissionsAndroid.requestMultiple([
        PermissionsAndroid.PERMISSIONS.CAMERA,
        PermissionsAndroid.PERMISSIONS.READ_EXTERNAL_STORAGE,
        PermissionsAndroid.PERMISSIONS.WRITE_EXTERNAL_STORAGE,
      ]);
      if (
        (await PermissionsAndroid.check('android.permission.CAMERA')) &&
        (await PermissionsAndroid.check(
          'android.permission.READ_EXTERNAL_STORAGE',
        )) &&
        (await PermissionsAndroid.check(
          'android.permission.WRITE_EXTERNAL_STORAGE',
        ))
      ) {
        console.log('ok');
        return true;
      }
      console.log('negado');
      return false;
    } catch (err) {
      console.warn(err);
      return false;
    }
  };
  
  react-native-image-picker ERROR: Couldn't get file path for photo 
  SOLVED: in launchCamera add to options -> { storageOptions: { privateDirectory: true } }
