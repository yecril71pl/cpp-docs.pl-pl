---
title: errno — Stałe
ms.date: 09/17/2018
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
ms.openlocfilehash: 34f92bedfa9606c90196f2e3a5e47dc341b23aea
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898745"
---
# <a name="errno-constants"></a>errno — Stałe

## <a name="syntax"></a>Składnia

```
#include <errno.h>
```

## <a name="remarks"></a>Uwagi

Wartości **errno** są stałymi przypisanymi do [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) w przypadku różnych warunków błędu.

ERRNO. H zawiera definicje wartości **errno** . Jednak nie wszystkie definicje zawarte w ERRNO. H są używane w 32-bitowych systemach operacyjnych Windows. Niektóre wartości w ERRNO. H jest obecny, aby zachować zgodność z rodziną systemów operacyjnych UNIX.

**Errno** wartości w 32-bitowym systemie operacyjnym Windows są podzbiorem wartości **errno** w systemach XENIX. W ten sposób wartość **errno** nie musi być taka sama jak rzeczywisty kod błędu zwracany przez wywołanie systemowe z systemów operacyjnych Windows. Aby uzyskać dostęp do rzeczywistego kodu błędu systemu operacyjnego, użyj zmiennej [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , która zawiera tę wartość.

Obsługiwane są następujące wartości **errno** :

|Stała|Opis|
|-|-|
|**ECHILD**|Brak procesów duplikowanych.|
|**EAGAIN**|Nie ma więcej procesów. Próba utworzenia nowego procesu nie powiodła się, ponieważ nie ma więcej miejsc przetwarzania lub nie ma wystarczającej ilości pamięci lub Osiągnięto maksymalny poziom zagnieżdżenia.|
|**E2BIG**|Lista argumentów jest za długa.|
|**EACCES**|Odmowa uprawnień. Ustawienie uprawnienia pliku nie zezwala na określony dostęp. Ten błąd oznacza, że podjęto próbę uzyskania dostępu do pliku (lub w niektórych przypadkach katalog) w taki sposób, który jest niezgodny z atrybutami pliku.<br/><br/>Na przykład błąd może wystąpić, gdy podjęto próbę odczytu z pliku, który nie jest otwarty, aby otworzyć istniejący plik tylko do odczytu do zapisu lub otworzyć katalog, a nie plik. W systemie operacyjnym MS-DOS w wersji 3,0 i nowszych **EACCES** może także wskazywać na naruszenie zasad blokowania lub udostępniania.<br/><br/>Ten błąd może również wystąpić podczas próby zmiany nazwy pliku lub katalogu lub usunięcia istniejącego katalogu.|
|**EBADF**|Zły numer pliku. Istnieją dwie możliwe przyczyny: 1) określony deskryptor pliku nie jest prawidłową wartością lub nie odwołuje się do otwartego pliku. 2) podjęto próbę zapisu w pliku lub urządzeniu otwartym na potrzeby dostępu tylko do odczytu.|
|**EDEADLOCK**|Wystąpił zakleszczenie zasobu. Argument funkcji matematycznej nie znajduje się w domenie funkcji.|
|**EDOM**|Argument matematyczny.|
|**EEXIST**|Istnieją pliki. Podjęto próbę utworzenia pliku, który już istnieje. Na przykład flagi **_O_CREAT** i **_O_EXCL** są określone w wywołaniu **_open** , ale nazwany plik już istnieje.|
|**EILSEQ**|Niedozwolona sekwencja bajtów (na przykład w ciągu MBCS).|
|**EINVAL**|Nieprawidłowy argument. Podano nieprawidłową wartość dla jednego z argumentów funkcji. Na przykład wartość podaną dla źródła podczas pozycjonowania wskaźnika pliku (za pomocą wywołania **fseek**) jest przed początkiem pliku.|
|**EMFILE**|Zbyt wiele otwartych plików. Nie ma więcej dostępnych deskryptorów plików, więc nie można otworzyć więcej plików.|
|**ENOENT**|Nie ma takiego pliku lub katalogu. Określony plik lub katalog nie istnieje lub nie można go znaleźć. Ten komunikat może wystąpić, gdy określony plik nie istnieje lub składnik ścieżki nie określa istniejącego katalogu.|
|**ENOEXEC**|Błąd formatu exec. Podjęto próbę wykonania pliku, który nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM**|Brak wystarczającej liczby rdzeni. Za mało dostępnej pamięci dla podjętych operatorów. Na przykład ten komunikat może wystąpić, gdy dostępna jest niewystarczająca ilość pamięci do wykonania procesu podrzędnego lub gdy nie można spełnić żądania alokacji w wywołaniu **_getcwd** .|
|**ENOSPC**|Brak miejsca na urządzeniu. Na urządzeniu nie ma więcej miejsca do zapisu (na przykład gdy dysk jest pełny).|
|**ERANGE**|Wynik jest za duży. Argument funkcji matematycznej jest zbyt duży, co spowoduje częściowe lub całkowite utratę istotności w wyniku. Ten błąd może również wystąpić w innych funkcjach, gdy argument jest większy niż oczekiwany (na przykład, gdy argument *buforu* do **_getcwd** jest dłuższy niż oczekiwany).|
|**EXDEV**|Łącze między urządzeniami. Podjęto próbę przeniesienia pliku do innego urządzenia (przy użyciu funkcji **zmiany nazwy** ).|
|**STRUNCATE**|Kopiowanie ciągu lub łączenie spowodowało przecięcie ciągu. Zobacz [_TRUNCATE](../c-runtime-library/truncate.md).

Poniższe wartości są obsługiwane w celu zapewnienia zgodności z systemem POSIX. Są to wymagane wartości w systemach innych niż POSIX.

```C
#define E2BIG /* argument list too long */
#define EACCES /* permission denied */
#define EADDRINUSE /* address in use */
#define EADDRNOTAVAIL /* address not available */
#define EAFNOSUPPORT /* address family not supported */
#define EAGAIN /* resource unavailable try again */
#define EALREADY /* connection already in progress */
#define EBADF /* bad file descriptor */
#define EBADMSG /* bad message */
#define EBUSY /* device or resource busy */
#define ECANCELED /* operation canceled */
#define ECHILD /* no child process */
#define ECONNABORTED /* connection aborted */
#define ECONNREFUSED /* connection refused */
#define ECONNRESET /* connection reset */
#define EDEADLK /* resource deadlock would occur */
#define EDESTADDRREQ /* destination address required */
#define EDOM /* argument out of domain */
#define EEXIST /* file exists */
#define EFAULT /* bad address */
#define EFBIG /* file too large */
#define EHOSTUNREACH /* host unreachable */
#define EIDRM /* identifier removed */
#define EILSEQ /* illegal byte sequence */
#define EINPROGRESS /* operation in progress */
#define EINTR /* interrupted */
#define EINVAL /* invalid argument */
#define EIO /* io error */
#define EISCONN /* already connected */
#define EISDIR /* is a directory */
#define ELOOP /* too many synbolic link levels */
#define EMFILE /* too many files open */
#define EMLINK /* too many links */
#define EMSGSIZE /* message size */
#define ENAMETOOLONG /* filename too long */
#define ENETDOWN /* network down */
#define ENETRESET /* network reset */
#define ENETUNREACH /* network unreachable */
#define ENFILE /* too many files open in system */
#define ENOBUFS /* no buffer space */
#define ENODATA /* no message available */
#define ENODEV /* no such device */
#define ENOENT /* no such file or directory */
#define ENOEXEC /* executable format error */
#define ENOLCK /* no lock available */
#define ENOLINK /* no link */
#define ENOMEM /* not enough memory */
#define ENOMSG /* no message */
#define ENOPROTOOPT /* no protocol option */
#define ENOSPC /* no space on device */
#define ENOSR /* no stream resources */
#define ENOSTR /* not a stream */
#define ENOSYS /* function not supported */
#define ENOTCONN /* not connected */
#define ENOTDIR /* not a directory */
#define ENOTEMPTY /* directory not empty */
#define ENOTRECOVERABLE /* state not recoverable */
#define ENOTSOCK /* not a socket */
#define ENOTSUP /* not supported */
#define ENOTTY /* inappropriate io control operation */
#define ENXIO /* no such device or address */
#define EOPNOTSUPP /* operation not supported */
#define EOTHER /* other */
#define EOVERFLOW /* value too large */
#define EOWNERDEAD /* owner dead */
#define EPERM /* operation not permitted */
#define EPIPE /* broken pipe */
#define EPROTO /* protocol error */
#define EPROTONOSUPPORT /* protocol not supported */
#define EPROTOTYPE /* wrong protocol type */
#define ERANGE /* result out of range */
#define EROFS /* read only file system */
#define ESPIPE /* invalid seek */
#define ESRCH /* no such process */
#define ETIME /* stream timeout */
#define ETIMEDOUT /* timed out */
#define ETXTBSY /* text file busy */
#define EWOULDBLOCK /* operation would block */
#define EXDEV /* cross device link */
```

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)
