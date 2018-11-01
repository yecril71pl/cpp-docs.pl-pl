---
title: Ostrzeżenie LNK4098 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 088124fcce7cafad3fab3280ae0b3ae0d893283e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468721"
---
# <a name="linker-tools-warning-lnk4098"></a>Ostrzeżenie LNK4098 narzędzi konsolidatora

użycie "library" defaultlib w konflikcie z innymi bibliotekami; Użyj /NODEFAULTLIB:library

Próbujesz połączyć się z bibliotekami niezgodne.

> [!NOTE]
>  Biblioteki wykonawcze zawierają teraz dyrektywy, aby zapobiec mieszaniu różnych typów. W tym samym programie otrzyma tego ostrzeżenia, Jeśli spróbujesz użyć różnych typów lub debugowania i bez debugowania wersji biblioteki wykonawczej. Na przykład jeśli skompilowano jeden plik do korzystania z jednego rodzaju biblioteki wykonawczej specyficznej innego pliku używać innego typu (na przykład jednowątkowe a wielowątkowe) i próbował łączyć je otrzymasz to ostrzeżenie. Należy skompilować wszystkich plików źródłowych przy użyciu tej samej biblioteki wykonawczej. Zobacz [korzystaj z bibliotek wykonawczych](../../build/reference/md-mt-ld-use-run-time-library.md) (**/MD**, **/MT**, **/LD**) opcje kompilatora, aby uzyskać więcej informacji.

Możesz użyć konsolidatora [opisu](../../build/reference/verbose-print-progress-messages.md) przełącznik, aby określić, które biblioteki, program łączący się wyszukiwanie. Jeśli zostanie wyświetlony LNK4098 i chcesz, aby utworzyć plik wykonywalny, który używa, na przykład jednowątkowe, bez debugowania biblioteki wykonawczej, należy użyć **opisu** opcję, aby dowiedzieć się, które biblioteki, program łączący się wyszukiwanie. Konsolidator powinien drukowanie LIBC.lib i nie LIBCMT.lib, MSVCRT.lib, LIBCD.lib, biblioteki LIBCMTD.lib lub biblioteki MSVCRTD.lib jako przeszukiwane biblioteki. Można stwierdzić, konsolidator, aby Ignoruj nieprawidłowe biblioteki czasu wykonywania przy użyciu [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) dla każdej biblioteki, aby zignorować.

W poniższej tabeli przedstawiono, które biblioteki należy zignorować w zależności od tego, które biblioteki czasu wykonywania, do którego chcesz użyć.

|Aby użyć tej biblioteki wykonawczej|Ignoruj te biblioteki|
|-----------------------------------|----------------------------|
|Jednowątkowe (libc.lib)|biblioteki libcmt.lib msvcrt.lib, libcd.lib, libcmtd.lib, biblioteki msvcrtd.lib|
|Wielowątkowe (libcmt.lib)|libc.lib msvcrt.lib, libcd.lib, libcmtd.lib, biblioteki msvcrtd.lib|
|Wielowątkowe przy użyciu biblioteki DLL (msvcrt.lib)|libc.lib libcmt.lib, libcd.lib, libcmtd.lib, biblioteki msvcrtd.lib|
|Jednowątkowe debugowania (libcd.lib)|libc.lib libcmt.lib, msvcrt.lib, libcmtd.lib, biblioteki msvcrtd.lib|
|Debuguj wielowątkowe (libcmtd.lib)|libc.lib libcmt.lib, msvcrt.lib, libcd.lib, biblioteki msvcrtd.lib|
|Debuguj wielowątkowe przy użyciu biblioteki DLL (msvcrtd.lib)|libc.lib libcmt.lib, msvcrt.lib, libcd.lib, biblioteki libcmtd.lib|

Na przykład jeśli chcesz utworzyć plik wykonywalny, który używa-debug, jednowątkowe wersji biblioteki wykonawczej otrzymany to ostrzeżenie, można użyć następujących opcji za pomocą konsolidatora:

```
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```