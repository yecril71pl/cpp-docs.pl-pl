---
title: '&lt;wyliczenia systemu&gt; plików'
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
ms.openlocfilehash: 0d5b31b31f9f435c52db89521b4b753c16d86501
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368413"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;wyliczenia systemu&gt; plików

W tym temacie dokumentuje wyliczenia w nagłówku systemu plików.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<eksperymentalny/system plików>

**Obszar nazw:** std::experimental::system plików

## <a name="copy_options"></a><a name="copy_options"></a>copy_options

Wyliczenie wartości maski bitowej używanej z funkcjami [kopiowania](filesystem-functions.md#copy) i [copy_file](filesystem-functions.md#copy_file) w celu określenia zachowania.

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
|`skip_existing`|Nie kopiuj, jeśli plik już istnieje, nie zgłaszaj błędu.|
|`overwrite_existing`|Zastąp plik, jeśli już istnieje.|
|`update_existing`|Zastąp plik, jeśli już istnieje i jest starszy niż zamiennik.|
|`recursive`|Rekursyjnie kopiuj podkatalogi i ich zawartość.|
|`copy_symlinks`|Skopiuj dołącza symboliczne jako dowiązanie symboliczne, zamiast kopiować pliki, na które wskazują.|
|`skip_symlinks`|Ignoruj dowiązania symboliczne.|
|`directories_only`|Tylko iterować nad katalogami, ignorować pliki.|
|`create_symlinks`|Zamiast kopiować pliki, można tworzyć łącza symboliczne. Ścieżka bezwzględna musi być używana jako ścieżka źródłowsza, chyba że miejscem docelowym jest bieżący katalog.|
|`create_hard_links`|Zamiast kopiować pliki, łącz się z twardymi łączami.|

## <a name="directory_options"></a><a name="directory_options"></a>directory_options

Określa, czy należy obserwować łącza symboliczne do katalogów, czy je ignorować.

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
|`none`|Domyślne zachowanie: ignoruj dowiązania symboliczne do katalogów. Odmowa uprawnień jest błędem.|
|`follow_directory_symlink`|Potraktuj symboliczne linki do katalogów jako rzeczywiste katalogi.|

## <a name="file_type"></a><a name="file_type"></a>file_type

Wyliczenie dla typów plików. Obsługiwane wartości są regularne, katalog, not_found i nieznane.

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
|`none`|0|Reprezentuje plik, który nie ma atrybutu typu. (Nie jest obsługiwany.)|
|`regular`|1|Reprezentuje konwencjonalny plik dysku.|
|`directory`|2|Reprezentuje katalog.|
|`symlink`|3|Reprezentuje dowiązanie symboliczne. (Nie jest obsługiwany.)|
|`block`|4|Reprezentuje plik specjalny blok w systemach opartych na systemie UNIX. (Nie jest obsługiwany.)|
|`character`|5|Reprezentuje plik znaków specjalnych w systemach opartych na systemie UNIX. (Nie jest obsługiwany.)|
|`fifo`|6|Reprezentuje plik FIFO w systemach opartych na systemie UNIX. (Nie jest obsługiwany.)|
|`socket`|7|Reprezentuje gniazdo w systemach opartych na uniksie. (Nie jest obsługiwany.)|
|`unknown`|8|Reprezentuje plik, którego stanu nie można określić.|

## <a name="perm_options"></a><a name="perm_options"></a>perm_options

Zawiera `replace`wartości `add` `remove`, `nofollow`, i .

```cpp
enum class perm_options;
```

## <a name="perms"></a><a name="perms"></a>perms

Flagi dla uprawnień do plików. Obsługiwane wartości są zasadniczo "tylko do odczytu" i wszystkie. W przypadku pliku tylko do odczytu nie ustawiono żadnych bitów *_write. W `all` przeciwnym razie bit (0x0777) jest ustawiony.

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

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>systemu plików](../standard-library/filesystem.md)
