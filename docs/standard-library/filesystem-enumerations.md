---
title: '&lt;System plików&gt; wyliczenia'
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
ms.openlocfilehash: 9c4efa145455240c4420a51c4a01662a30dc0761
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405134"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;System plików&gt; wyliczenia

Tym temacie omówiono typy wyliczeniowe w nagłówku systemu plików.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<eksperymentalne/filesystem >

**Namespace:** std::experimental::filesystem

## <a name="copy_options"></a>  copy_options

Wyliczenie wartości masek bitowych, które jest używane z [kopiowania](filesystem-functions.md#copy) i [copy_file —](filesystem-functions.md#copy_file) funkcji do określenia zachowania.

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
|`none`|Wykonaj domyślne zachowanie dla tej operacji.|
|`skip_existing`|Nie Kopiuj, jeśli plik już istnieje, nie będą zgłaszać błąd.|
|`overwrite_existing`|Zastąp plik, jeśli już istnieje.|
|`update_existing`|Zastąp plik, jeśli już istnieje i jest starsza niż zastąpienia.|
|`recursive`|Rekursywnie skopiować podkatalogów i ich zawartość.|
|`copy_symlinks`|Kopiowanie łącza symbolicznego, jako łącza symbolicznego, zamiast kopiować pliki na które one wskazują.|
|`skip_symlinks`|Ignoruj łącza symbolicznego.|
|`directories_only`|Tylko iteracyjne przeglądanie katalogów, plików do ignorowania.|
|`create_symlinks`|Należy łącza symbolicznego, zamiast kopiować pliki. Ścieżka bezwzględna musi służyć jako ścieżki źródłowej, chyba że miejsce docelowe jest bieżący katalog.|
|`create_hard_links`|Należy twardych linków zamiast kopiować pliki.|

## <a name="directory_options"></a> directory_options —

Określa, czy linki symboliczne z katalogami lub je ignorować.

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
|`none`|Domyślne zachowanie: Ignoruj łącza symbolicznego do katalogów. Odmowa uprawnień, występuje błąd.|
|`follow_directory_symlink`|Traktuj linki symboliczne do katalogów jako rzeczywisty katalogów.|

## <a name="file_type"></a>  file_type —

Wyliczenie dla typów plików. Obsługiwane wartości to zwykłych, katalog, not_found i nieznany.

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
|`none`|0|Reprezentuje plik, który nie ma typu atrybutu. (Nie są obsługiwane.)|
|`regular`|1|Reprezentuje plik konwencjonalne dysku.|
|`directory`|2|Reprezentuje katalog.|
|`symlink`|3|Reprezentuje łącze symboliczne. (Nie są obsługiwane.)|
|`block`|4|Reprezentuje plik specjalny bloku na komputerach z systemem UNIX. (Nie są obsługiwane.)|
|`character`|5|Reprezentuje plik znaków specjalnych, na komputerach z systemem UNIX. (Nie są obsługiwane.)|
|`fifo`|6|Reprezentuje plik FIFO na komputerach z systemem UNIX. (Nie są obsługiwane.)|
|`socket`|7|Reprezentuje gniazda na komputerach z systemem UNIX, na podstawie. (Nie są obsługiwane.)|
|`unknown`|8|Reprezentuje plik, którego stan nie może być określony.|

## <a name="perms"></a>  PERMS

Flagi, aby uzyskać uprawnienia do pliku. Obsługiwane wartości to zasadniczo "readonly" i wszystkie. Dla pliku tylko do odczytu, żaden z * _write bity są ustawione. W przeciwnym razie `all` ustawiony bit (0x0777).

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

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
