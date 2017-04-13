7. Установка плагина в терминал Quik

7.1. В директории терминала Quik создаем копию *lua51.dll* от Arqa и называем ее *lua5.1.dll*, для соответствия идентификаторам, используемым в родном lua5.1.lib, который мы скачивали на этапе установки библиотек.

7.2. Копируем скомпилированный файл плагина *lualib_qluacpp_tutorial.dll* в директорию Quik

7.3. Создаем lua-скрипт *qluacpp_tutorial.lua*, грузящий нашу "библиотеку Lua" и содержащий единственную строку:
```lua
require "lualib_qluacpp_tutorial"
```