---
title: Ostrzeżenie LNK4098 narzędzi konsolidatora
ms.date: 03/26/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 66cf1a1bc75405ffc9bae8158bfc8682776a8228
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508731"
---
# <a name="linker-tools-warning-lnk4098"></a>Ostrzeżenie LNK4098 narzędzi konsolidatora

> defaultlib "*biblioteki*" powoduje konflikt z innymi bibliotekami; Użyj/nodefaultlib:*biblioteki*

Próbujesz połączyć się z bibliotekami niezgodne.

> [!NOTE]
> Biblioteki wykonawcze zawierają teraz dyrektywy, aby zapobiec mieszaniu różnych typów. W tym samym programie otrzyma tego ostrzeżenia, Jeśli spróbujesz użyć różnych typów lub debugowania i bez debugowania wersji biblioteki wykonawczej. Na przykład, jeśli skompilowany jeden plik, aby użyć jednego rodzaju biblioteki wykonawczej i inny plik używać innego typu (na przykład debug i sprzedaży detalicznej) i próbował łączyć je, otrzymasz ostrzeżenie. Należy skompilować wszystkich plików źródłowych przy użyciu tej samej biblioteki wykonawczej. Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Korzystaj z bibliotek wykonawczych)](../../build/reference/md-mt-ld-use-run-time-library.md) opcje kompilatora.

Możesz użyć konsolidatora [opisu](../../build/reference/verbose-print-progress-messages.md) przełącznika, aby dowiedzieć się, które biblioteki wyszukiwania konsolidatora. Na przykład gdy plik wykonywalny używa biblioteki wykonawczej wielowątkowych, -debug, lista zgłoszonych powinna zawierać LIBCMT.lib, a nie LIBCMTD.lib, MSVCRT.lib lub biblioteki MSVCRTD.lib. Można stwierdzić, konsolidator, aby Ignoruj nieprawidłowe biblioteki czasu wykonywania przy użyciu [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) dla każdej biblioteki, aby zignorować.

W poniższej tabeli przedstawiono, które biblioteki należy zignorować w zależności od tego, które biblioteki czasu wykonywania, do którego chcesz użyć. W wierszu polecenia, użyj jednej **/nodefaultlib** opcję dla wszystkich bibliotek do zignorowania. W programie Visual Studio IDE, oddzielnych bibliotek do zignorowania średnikami w **Ignoruj określone biblioteki domyślne** właściwości.

| Aby użyć tej biblioteki wykonawczej | Ignoruj te biblioteki |
|-----------------------------------|----------------------------|
| Wielowątkowe (libcmt.lib) | msvcrt.lib; libcmtd.lib; msvcrtd.lib |
| Wielowątkowe przy użyciu biblioteki DLL (msvcrt.lib) | libcmt.lib; libcmtd.lib; msvcrtd.lib |
| Debuguj wielowątkowe (libcmtd.lib) | libcmt.lib; msvcrt.lib; msvcrtd.lib |
| Debuguj wielowątkowe przy użyciu biblioteki DLL (msvcrtd.lib) | libcmt.lib; msvcrt.lib; libcmtd.lib |

Na przykład Odebrano to ostrzeżenie, jeśli chcesz utworzyć plik wykonywalny, korzysta z wersji biblioteki DLL bez debugowania biblioteki wykonawczej, za pomocą konsolidatora, można użyć następujących opcji:

```cmd
/NODEFAULTLIB:libcmt.lib NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```