# HostPoint-MiniFilter-Driver
Драйвер МиниФильтр файловой системы.
Код написан в MS Visual Studio 2013.

Основное назначение:
Преднастроенная блокировка операций с файлами на уровне ядра Операционных систем Windows.

Имеет следующие функции:
1. Полную блокировку всех операций с файлами
2. Частичную блокировку операций с файлами
- Загрузку всех программ
- Открытие файлов программами на редактирование
- Чтение/запись файлов программами

Блокировка возможна как для всех, либо для определенных пользователей или программ, а так же по расширениям файлов.
________________________________________________________________________________________________________________________
Настройка работы драйвера производится через системный Реестр Windows - "\\Registry\\Machine\\SOFTWARE\\ControlSystem"
________________________________________________________________________________________________________________________
Ключи реестра:
1. Блокировка операций на USB накопителях - "GlobalLockUSB": (REG_DWORD) 0/1
2. Блокировка запуска процесса на логическом диске - "LockProcExecuteLocal": (REG_DWORD) 0/1
3. Блокировка запуска процесса на USB накопителях - "LockProcExecuteUSB": (REG_DWORD) 0/1
4. Блокировка работы с файлами имеющими расширения на USB накомителях - "FileExtensionsLockUSB": (REG_MULTI_SZ) ".tiff .jpg"
5. Блокировка всех операций процессов на USB накомителях - "ProcNameLockUSB": (REG_MULTI_SZ) "calc.exe word.exe"
6. Блокировка всех операций пользователей на USB накомителях - "UserNameLockUSB": (REG_MULTI_SZ) "ivanov petrov"
7. Блокировка работы с файлами имеющими расширения на локальных логических дисках - "FileExtensionsLockLocal": (REG_MULTI_SZ) ".tiff .jpg"
8. Блокировка всех операций процессов на локальных логических дисках - "ProcNameLockLocal": (REG_MULTI_SZ) "calc.exe word.exe"
9. Блокировка всех операций пользователей на локальных логических дисках - "UserNameLockLocal": (REG_MULTI_SZ) "ivanov petrov"
10.Блокировка запуска определенных программ с USB накопителя - "ProcNameLockExecUSB": (REG_MULTI_SZ) "calc.exe word.exe"
11.Блокировка запуска программ под определенными пользователями - "UserNameLockExecUSB": (REG_MULTI_SZ) "ivanov petrov"
12.Блокировка запуска определенных программ с локальных логических дисков - "ProcNameLockExecLocal": (REG_MULTI_SZ) "calc.exe word.exe"
13.Блокировка запуска программ под определенными пользователями с локальных логических дисков - "UserNameLockExecLocal": (REG_MULTI_SZ) "ivanov"
14. Путь к логам - "DLPLogPath" (если параметр не определен в реестре, логи операций пишутся в "\\%SystemRoot%\\HostPointDLP.logs")

Драйвер собирается под MS Visual Studio 2013/2017.
Для сборки требуется установленный - "WindowsKernelModeDriver8.1" (https://docs.microsoft.com/en-us/windows-hardware/drivers/devtest/platform-toolset)
