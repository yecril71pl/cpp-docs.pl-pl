---
title: errno — stałe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ebcb694c962b30ff923e65b4a1ebb411f2bf6dd9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392175"
---
# <a name="errno-constants"></a>errno — Stałe
## <a name="syntax"></a>Składnia  
  
```  
  
#include <errno.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 **Errno** wartości są stałe przypisane do [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) w przypadku różnych warunków błędów.  
  
 NUMER BŁĘDU. H zawiera definicje **errno** wartości. Jednakże, nie wszystkie definicje podane w numer błędu. H są używane w 32-bitowych systemach operacyjnych Windows. Niektóre wartości w numer błędu. H znajdują się w celu utrzymania zgodności z rodziny systemów operacyjnych UNIX.  
  
 **Errno** wartości w 32-bitowym systemie operacyjnym Windows są podzbiorem wartości **errno** w systemach XENIX. W związku z tym **errno** wartość nie jest zawsze taki sam, jak kod błędu zwrócony przez wywołanie systemu z systemów operacyjnych Windows. Aby uzyskać dostęp do kod błędu systemu operacyjnego, należy użyć [_doserrno —](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) zmiennej, która zawiera tę wartość.  
  
 Następujące **errno** wartości są obsługiwane:  
  
 **ECHILD —**  
 Nie uruchomionego procesu.  
  
 **EAGAIN —**  
 Żadne procesy więcej. Próba utworzenia nowego procesu nie powiodła się, ponieważ nie ma żadnych kolejnych gniazd proces nie ma wystarczającej ilości pamięci lub osiągnięto maksymalny poziom zagnieżdżenia.  
  
 **E2BIG —**  
 Lista argumentów jest za długa.  
  
 **EACCES**  
 Odmowa uprawnień. Ustawienie uprawnień pliku nie zezwala na dostęp określonym. Ten błąd oznacza, że nastąpiła próba dostępu do pliku (lub, w niektórych przypadkach katalog) w sposób niezgodny z atrybutów pliku.  
  
 Na przykład ten błąd może wystąpić podczas próby odczytu z pliku, który nie jest otwarty, otwórz istniejący plik tylko do odczytu do zapisu lub otwórz katalog, nie plikiem. W wersjach systemu operacyjnego systemu MS-DOS 3.0 i nowszych **eacces —** może również oznaczać blokowanie lub naruszenie zasad współużytkowania.  
  
 Ten błąd może również wystąpić w próbę zmiany nazwy pliku lub katalogu lub usuń istniejący katalog.  
  
 **EBADF —**  
 Liczba uszkodzonych plików. Istnieją dwie możliwe przyczyny: 1) deskryptora określony plik nie jest prawidłową wartością lub nie można znaleźć otwartego pliku. 2) została podjęta próba zapisu do pliku lub otwarta z dostępem tylko do odczytu do urządzenia.  
  
 **EDEADLOCK —**  
 Wystąpiłoby zakleszczenie zasobu. Argument funkcji matematycznych nie jest w domenie funkcji.  
  
 **EDOM —**  
 Argument matematycznych.  
  
 **EEXIST —**  
 Pliki istnieją. Nastąpiła próba do utworzenia pliku, który już istnieje. Na przykład **_o_creat —** i **_o_excl —** flagi są określone w **_otwórz** wywołanie, ale wskazanego pliku już istnieje.  
  
 **EILSEQ —**  
 Niedozwolony sekwencję bajtów (na przykład w postaci ciągu MBCS).  
  
 **EINVAL —**  
 Nieprawidłowy argument. Dla jednego z argumentów do funkcji podano nieprawidłową wartość. Przykładowo, podana wartość dla źródła podczas rozmieszczania wskaźnika pliku (za pomocą wywołania **fseek**) jest przed początkiem pliku.  
  
 **EMFILE —**  
 Zbyt wiele otwartych plików. Nie więcej deskryptorów plików są dostępne, więc nie ma więcej plików można otworzyć.  
  
 **ENOENT —**  
 Brak pliku lub katalogu. Określony plik lub katalog nie istnieje lub nie można odnaleźć. Ten komunikat może wystąpić, gdy określony plik nie istnieje lub składnika ścieżki nie Określ istniejący katalog.  
  
 **ENOEXEC —**  
 Błąd formatu pliku wykonywalnego. Próbowano wykonać pliku, który nie jest wykonywalne lub który ma nieprawidłowy format pliku wykonywalnego.  
  
 **ENOMEM —**  
 Nie ma wystarczającej liczby rdzeni. Za mało pamięci dostępnej dla operatora próby. Na przykład ten komunikat może wystąpić, gdy ma wystarczającej ilości pamięci do wykonania procesu podrzędnego lub gdy żądanie alokacji w **_getcwd —** wywołania nie mogą być spełnione.  
  
 **ENOSPC —**  
 Nie ma wolnego miejsca na urządzeniu. Miejsca do zapisu jest dostępny na urządzeniu (na przykład, gdy dysk jest pełny).  
  
 **ERANGE —**  
 Wynik jest za duży. Argument funkcji matematycznych jest zbyt duży, co grozi utratą częściowe lub całkowite znaczenie w wyniku. Ten błąd może również wystąpić w innych funkcjach, gdy argument jest większy niż oczekiwano (na przykład, gdy *buforu* argument **_getcwd —** jest dłuższa niż oczekiwano).  
  
 **EXDEV**  
 Łącze między urządzeniami. Podjęto próbę przeniesienia pliku do innego urządzenia (przy użyciu **zmienić** funkcji).  
  
 **STRUNCATE —**  
 Kopia ciągu lub łączenia spowodowała ciągu obcięte. Zobacz [_truncate —](../c-runtime-library/truncate.md).  
  
 Następujące wartości są obsługiwane w celu zapewnienia zgodności z Posix. Są one wymagane wartości w systemach z systemem innym niż Posix.  
  
```  
#define E2BIG [argument list too long]  
#define EACCES [permission denied]  
#define EADDRINUSE [address in use]  
#define EADDRNOTAVAIL [address not available]  
#define EAFNOSUPPORT [address family not supported]  
#define EAGAIN [resource unavailable try again]  
#define EALREADY [connection already in progress]  
#define EBADF [bad file descriptor]  
#define EBADMSG [bad message]  
#define EBUSY [device or resource busy]  
#define ECANCELED [operation canceled]  
#define ECHILD [no child process]  
#define ECONNABORTED [connection aborted]  
#define ECONNREFUSED [connection refused]  
#define ECONNRESET [connection reset]  
#define EDEADLK [resource deadlock would occur]  
#define EDESTADDRREQ [destination address required]  
#define EDOM [argument out of domain]  
#define EEXIST [file exists]  
#define EFAULT [bad address]  
#define EFBIG [file too large]  
#define EHOSTUNREACH [host unreachable]  
#define EIDRM [identifier removed]  
#define EILSEQ [illegal byte sequence]  
#define EINPROGRESS [operation in progress]  
#define EINTR [interrupted]  
#define EINVAL [invalid argument]  
#define EIO [io error]  
#define EISCONN [already connected]  
#define EISDIR [is a directory]  
#define ELOOP [too many synbolic link levels]  
#define EMFILE [too many files open]  
#define EMLINK [too many links]  
#define EMSGSIZE [message size]  
#define ENAMETOOLONG [filename too long]  
#define ENETDOWN [network down]  
#define ENETRESET [network reset]  
#define ENETUNREACH [network unreachable]  
#define ENFILE [too many files open in system]  
#define ENOBUFS [no buffer space]  
#define ENODATA [no message available]  
#define ENODEV [no such device]  
#define ENOENT [no such file or directory]  
#define ENOEXEC [executable format error]  
#define ENOLCK [no lock available]  
#define ENOLINK [no link]  
#define ENOMEM [not enough memory]  
#define ENOMSG [no message]  
#define ENOPROTOOPT [no protocol option]  
#define ENOSPC [no space on device]  
#define ENOSR [no stream resources]  
#define ENOSTR [not a stream]  
#define ENOSYS [function not supported]  
#define ENOTCONN [not connected]  
#define ENOTDIR [not a directory]  
#define ENOTEMPTY [directory not empty]  
#define ENOTRECOVERABLE [state not recoverable]  
#define ENOTSOCK [not a socket]  
#define ENOTSUP [not supported]  
#define ENOTTY [inappropriate io control operation]  
#define ENXIO [no such device or address]  
#define EOPNOTSUPP [operation not supported]  
#define EOTHER [other]  
#define EOVERFLOW [value too large]  
#define EOWNERDEAD [owner dead]  
#define EPERM [operation not permitted]  
#define EPIPE [broken pipe]  
#define EPROTO [protocol error]  
#define EPROTONOSUPPORT [protocol not supported]  
#define EPROTOTYPE [wrong protocol type]  
#define ERANGE [result out of range]  
#define EROFS [read only file system]  
#define ESPIPE [invalid seek]  
#define ESRCH [no such process]  
#define ETIME [stream timeout]  
#define ETIMEDOUT [timed out]  
#define ETXTBSY [text file busy]  
#define EWOULDBLOCK [operation would block]  
#define EXDEV [cross device link]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe globalne](../c-runtime-library/global-constants.md)