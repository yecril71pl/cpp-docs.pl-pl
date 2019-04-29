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
ms.openlocfilehash: 0e11c11b468ff6e058ccf5c75b000396e0473bfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343839"
---
# <a name="errno-constants"></a>errno — Stałe

## <a name="syntax"></a>Składnia

```
#include <errno.h>
```

## <a name="remarks"></a>Uwagi

**Errno** wartości są przypisane do stałych [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) w przypadku różnych warunków błędów.

NUMER BŁĘDU. H zawiera definicje **errno** wartości. Jednakże, nie wszystkie definicje, które są podane w numer błędu. H są używane w 32-bitowych systemach operacyjnych Windows. Niektóre wartości w numer błędu. H znajdują się zachować zgodność z systemów operacyjnych z rodziny systemu UNIX.

**Errno** wartości w 32-bitowym systemie operacyjnym Windows stanowią podzestaw wartości **errno** w systemach XENIX. W efekcie **errno** wartość niekoniecznie jest taka sama jak faktyczny kod błędu zwrócony przez wywołanie systemowe z systemów operacyjnych Windows. Aby uzyskać dostęp do kod błędu systemu operacyjnego, należy użyć [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) zmienną, która zawiera tę wartość.

Następujące **errno** wartości są obsługiwane:

|Stała|Opis|
|-|-|
|**ECHILD**|Brak procesów zduplikowanych.|
|**EAGAIN**|Brak procesów. Próba utworzenia nowego procesu nie powiodło się, ponieważ nie ma żadnych kolejnych gniazd procesu, nie ma wystarczającej ilości pamięci lub osiągnięto maksymalny poziom zagnieżdżenia.|
|**E2BIG**|Lista argumentów jest za długa.|
|**EACCES**|Odmowa uprawnień. Ustawienie uprawnienia pliku zezwalają na dostęp określonym. Ten błąd oznacza, że podjęto próbę uzyskania dostępu do pliku (lub w niektórych przypadkach katalogu) w sposób niezgodny z atrybutami plików.<br/><br/>Na przykład ten błąd może wystąpić, gdy podejmowana jest próba odczytu z pliku, który nie jest otwarty, otwórz istniejący plik tylko do odczytu do zapisu lub otwórz katalog, a nie plikiem. W obszarze MS-DOS systemu operacyjnego wersji 3.0 lub nowszej **EACCES** może również wskazywać blokowanie lub naruszenie zasad współużytkowania.<br/><br/>Ten błąd może również wystąpić podczas próby zmiany nazwy pliku lub katalogu lub usuń istniejący katalog.|
|**EBADF**|Zły numer pliku. Istnieją dwie możliwe przyczyny: (1) w deskryptorze określony plik nie jest prawidłową wartością lub odwołuje się do otwartego pliku. (2) podjęto można zapisać do pliku lub urządzenia, na dostęp tylko do odczytu.|
|**EDEADLOCK**|Wystąpiłoby zakleszczenie zasobu. Argument funkcji matematycznych, nie znajduje się w domenie funkcji.|
|**EDOM**|Argument matematyczny.|
|**EEXIST**|Pliki istnieją. Podjęta próba utworzenia pliku, który już istnieje. Na przykład **_O_CREAT** i **_O_EXCL** flagi są określone w **_otwórz** wywołanie, ale plik o nazwie już istnieje.|
|**EILSEQ**|Nieprawidłowa sekwencja bajtów (na przykład w postaci ciągu MBCS).|
|**EINVAL**|Nieprawidłowy argument. Dla jednego z argumentów funkcji podano nieprawidłową wartość. Na przykład, wartość podana dla oryginalnej operacji, podczas pozycjonowania wskaźnik pliku (za pomocą wywołania **fseek**) jest wcześniejsza od początku pliku.|
|**EMFILE**|Zbyt wiele otwartych plików. Więcej deskryptorów plików nie są dostępne, więc nie ma więcej plików można otworzyć.|
|**ENOENT**|Nie ma takiego pliku lub katalogu. Określony plik lub katalog nie istnieje lub nie można odnaleźć. Ten komunikat może zostać określony plik nie istnieje lub składnika ścieżki nie określono istniejącego katalogu.|
|**ENOEXEC**|Błąd formatu pliku wykonywalnego. Próbowano wykonać pliku, który nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego.|
|**ENOMEM**|Nie ma wystarczającej liczby rdzeni. Nie ma wystarczającej ilości pamięci dostępnej dla operatora próba. Na przykład, ten komunikat może wystąpić, gdy ma wystarczającej ilości pamięci do wykonania procesu podrzędnego, lub gdy przydział zażądać **_getcwd —** wywołania nie mogą zostać spełnione.|
|**ENOSPC**|Nie miejsca na urządzeniu. Mało miejsca do zapisu jest dostępna na urządzeniu (na przykład, gdy dysk jest pełny).|
|**ERANGE**|Wynik jest za duży. Argument funkcji matematycznych jest zbyt duży, wynikiem częściowego lub całkowita utrata znaczenia w wyniku. Ten błąd może również wystąpić w innych funkcjach, gdy argument jest większy, niż oczekiwano (na przykład, gdy *buforu* argument **_getcwd —** trwa dłużej niż oczekiwano).|
|**EXDEV**|Łącze między urządzeniami. Nastąpiła próba można przenieść pliku do innego urządzenia (przy użyciu **Zmień nazwę** funkcji).|
|**STRUNCATE**|Kopia ciągu lub łączenia w wyniku ciągu obcięte. Zobacz [_TRUNCATE](../c-runtime-library/truncate.md).

Następujące wartości są obsługiwane na potrzeby utrzymywania zgodności z modelem Posix. Są one wymagane wartości w systemach innych Posix.

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
