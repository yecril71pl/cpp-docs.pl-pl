---
title: "&lt;System plików&gt; wyliczenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
dev_langs:
- C++
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6a6d7dcb0e0b0a8e655acbda0624f7fa5b70a8a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;System plików&gt; wyliczenia
W tym temacie omówiono typy wyliczeniowe w nagłówku systemu plików.

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<eksperymentalne/filesystem >    
 **Namespace:** std::experimental::filesystem  

##  <a name="copy_options"></a>  copy_options
Wyliczenie wartości maski bitów, które jest używane z [kopiowania](http://msdn.microsoft.com/en-us/4af7a9b0-8861-45ed-b84e-0307f0669d60) i [copy_file —](http://msdn.microsoft.com/en-us/4af7a9b0-8861-45ed-b84e-0307f0669d60) funkcji w celu określenia zachowania.  
  
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
|`skip_existing`|Nie należy kopiować, jeśli plik już istnieje, nie będą zgłaszać błąd.|  
|`overwrite_existing`|Zastąp plik, jeśli już istnieje.|  
|`update_existing`|Zastąp plik, jeśli już istnieje i jest starsza niż zastąpienia.|  
|`recursive`|Rekursywnie skopiować podkatalogi i ich zawartość.|  
|`copy_symlinks`|Skopiuj łącza symbolicznego jako łącza symbolicznego, zamiast kopiować pliki wskaż pozycję.|  
|`skip_symlinks`|Ignoruj łącza symbolicznego.|  
|`directories_only`|Tylko iteracja katalogów, ignorowania plików.|  
|`create_symlinks`|Należy łącza symbolicznego zamiast kopiować pliki. Ścieżka bezwzględna muszą być używane jako ścieżka źródłowa, chyba że docelowy jest to katalog bieżący.|  
|`create_hard_links`|Należy twardych łączy zamiast kopiować pliki.|  
  

##  <a name="directory_options"></a> directory_options —
Określa, czy linki symboliczne do katalogów lub można je zignorować.  
  
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
|`none`|Domyślne zachowanie: Ignoruj linki symboliczne do katalogów. Odmowa uprawnień, występuje błąd.|  
|`follow_directory_symlink`|Traktuj łącza symbolicznego katalogi jako rzeczywisty katalogów.|  
  
##  <a name="file_type"></a>  file_type —
Wyliczenie dla typów plików. Obsługiwane wartości to zwykły, katalog not_found i nieznany.  
  
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
|`none`|0|Reprezentuje plik, który nie ma typu atrybutu. (Nie jest obsługiwany.)|  
|`regular`|1|Reprezentuje plik z konwencjonalnej dysku.|  
|`directory`|2|Reprezentuje katalog.|  
|`symlink`|3|Reprezentuje łącze symboliczne. (Nie jest obsługiwany.)|  
|`block`|4|Reprezentuje plik specjalne bloku na komputerach z systemem UNIX. (Nie jest obsługiwany.)|  
|`character`|5|Reprezentuje plik znaków specjalnych w systemach UNIX. (Nie jest obsługiwany.)|  
|`fifo`|6|Reprezentuje plik FIFO na komputerach z systemem UNIX. (Nie jest obsługiwany.)|  
|`socket`|7|Reprezentuje gniazda na komputerach z systemem UNIX. (Nie jest obsługiwany.)|  
|`unknown`|8|Reprezentuje plik, którego stan nie można określić.|  
  
##  <a name="perms"></a>  PERMS
Flagi uprawnienia do pliku. Obsługiwane wartości to zasadniczo "readonly" i wszystkich. Dla pliku tylko do odczytu, żaden z * _write bity zostały ustawione. W przeciwnym razie `all` ustawiono bit (0x0777).  
  
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
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<FileSystem >](../standard-library/filesystem.md)

