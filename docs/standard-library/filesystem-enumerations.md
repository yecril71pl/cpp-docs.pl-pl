---
title: '&lt;wyliczenia&gt; systemu plików'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
ms.openlocfilehash: dfbcf65462f0bb7bc6ca44f43507efa7b753e7bc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457715"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;wyliczenia&gt; systemu plików

Ten temat dokumentuje wyliczenia w nagłówku systemu plików.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<eksperymentalny/> systemu plików

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="copy_options"></a>copy_options

Wyliczenie wartości masek bitowych, które są używane z funkcjami [copy](filesystem-functions.md#copy) i [copy_file](filesystem-functions.md#copy_file) , aby określić zachowanie.

### <a name="syntax"></a>Składnia

```cpp
enum class copy_options {
   none = 0,
   skip_existing = 1,
   overwrite_existing = 2,
   update_existing = 4,
   recursive = 8,
   copy_symlinks = 16,
   skip_symlinks = 32,
   directories_only = 64,
   create_symlinks = 128,
   create_hard_links = 256
};
```

### <a name="values"></a>Wartości

|`Name`|Opis|
|------------|-----------------|
|`none`|Wykonaj domyślne zachowanie dla operacji.|
|`skip_existing`|Nie Kopiuj, jeśli plik już istnieje, nie zgłaszaj błędu.|
|`overwrite_existing`|Zastąp plik, jeśli już istnieje.|
|`update_existing`|Zastąp plik, jeśli już istnieje i jest starszy niż zastąpienie.|
|`recursive`|Rekursywnie Kopiuj podkatalogi i ich zawartość.|
|`copy_symlinks`|Skopiuj linki symboliczne jako linki symboliczne, zamiast kopiować pliki, do których wskazują.|
|`skip_symlinks`|Ignoruj linki symboliczne.|
|`directories_only`|Wykonaj iterację tylko dla katalogów, Ignoruj pliki.|
|`create_symlinks`|Utwórz linki symboliczne zamiast kopiować pliki. Ścieżka bezwzględna musi być używana jako ścieżka źródłowa, chyba że miejsce docelowe jest bieżącym katalogiem.|
|`create_hard_links`|Twórz twarde linki zamiast kopiować pliki.|

## <a name="directory_options"></a>directory_options

Określa, czy mają być stosowane linki symboliczne do katalogów czy do ich ignorowania.

### <a name="syntax"></a>Składnia

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`none`|Zachowanie domyślne: Ignoruj linki symboliczne do katalogów. Odmowa uprawnień jest błędem.|
|`follow_directory_symlink`|Traktuj symboliczne linki do katalogów jako katalogi rzeczywiste.|

## <a name="file_type"></a>file_type

Wyliczenie dla typów plików. Obsługiwane wartości to regularne, katalog, not_found i nieznane.

### <a name="syntax"></a>Składnia

```cpp
enum class file_type {
    not_found = -1,
    none,
    regular,
    directory,
    symlink,
    block,
    character,
    fifo,
    socket,
    unknown
};
```

### <a name="values"></a>Wartości

|Nazwa|Wartość|Opis|
|----------|-----------|-----------------|
|`not_found`|-1|Reprezentuje plik, który nie istnieje.|
|`none`|0|Reprezentuje plik, który nie ma atrybutu Type. (Nieobsługiwane).|
|`regular`|1|Reprezentuje konwencjonalny plik dysku.|
|`directory`|2|Reprezentuje katalog.|
|`symlink`|3|Reprezentuje łącze symboliczne. (Nieobsługiwane).|
|`block`|4|Reprezentuje plik specjalny bloku w systemach opartych na systemie UNIX. (Nieobsługiwane).|
|`character`|5|Reprezentuje plik specjalny znaku w systemach opartych na systemie UNIX. (Nieobsługiwane).|
|`fifo`|6|Reprezentuje plik FIFO w systemach opartych na systemie UNIX. (Nieobsługiwane).|
|`socket`|7|Reprezentuje gniazdo w systemach opartych na systemie UNIX. (Nieobsługiwane).|
|`unknown`|8|Reprezentuje plik, którego stan nie może zostać określony.|

## <a name="perm_options"></a>perm_options

Obejmuje wartości `replace`, `add`, `remove`i .`nofollow`

```cpp
enum class perm_options;
```

## <a name="perms"></a>uprawnienia

Flagi uprawnień do plików. Obsługiwane wartości są zasadniczo "tylko do odczytu" i wszystkie. Dla pliku tylko do odczytu nie ustawiono żadnego z * _write bitów. W przeciwnym `all` razie jest ustawiona wartość bit (0x0777).

### <a name="syntax"></a>Składnia

```cpp
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)
