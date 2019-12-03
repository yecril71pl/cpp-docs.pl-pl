---
title: Ostrzeżenie LNK4098 narzędzi konsolidatora
description: Opisuje, w jaki sposób niezgodne biblioteki powodują ostrzeżenia narzędzi konsolidatora LNK4098 narzędzi KONSOLIDATORA, oraz sposób używania/NODEFAULTLIB do jego naprawy.
ms.date: 12/02/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 9d0c7da0614651a98d5ed4f3bd3676c7d837ce67
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682940"
---
# <a name="linker-tools-warning-lnk4098"></a>Ostrzeżenie LNK4098 narzędzi konsolidatora

> DEFAULTLIB "*Biblioteka*" powoduje konflikt z użyciem innych libs; Użyj/NODEFAULTLIB:*Library*

Próbujesz połączyć się z niezgodnymi bibliotekami.

> [!NOTE]
> Biblioteki czasu wykonywania zawierają teraz dyrektywy, które uniemożliwiają mieszanie różnych typów. To ostrzeżenie zostanie wyświetlone, jeśli spróbujesz użyć różnych typów lub debugowania i niedebugowanych wersji biblioteki wykonawczej w tym samym programie. Na przykład w przypadku skompilowania jednego pliku do użycia jednego rodzaju biblioteki wykonawczej i innego pliku do użycia innego rodzaju (na przykład debugowania i sprzedaży detalicznej) i nastąpiło połączenie, zostanie wyświetlone ostrzeżenie. Należy skompilować wszystkie pliki źródłowe, aby użyć tej samej biblioteki wykonawczej. Aby uzyskać więcej informacji, zobacz Opcje kompilatora [/MD,/MT,/LD (Use Run-Time Library)](../../build/reference/md-mt-ld-use-run-time-library.md) .

Aby dowiedzieć się, które biblioteki przeszukuje konsolidator, można użyć przełącznika [/verbose: lib](../../build/reference/verbose-print-progress-messages.md) . Na przykład, gdy plik wykonywalny używa wielowątkowych bibliotek czasu uruchomieniowego, lista raportowana powinna zawierać LIBCMT. lib, a nie LIBCMTD. lib, MSVCRT. lib lub MSVCRTD. lib. Możesz powiedzieć konsolidatorowi, aby zignorować niepoprawne biblioteki czasu wykonywania za pomocą [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) dla każdej biblioteki, która ma być ignorowana.

W poniższej tabeli przedstawiono biblioteki, które powinny być ignorowane w zależności od biblioteki wykonawczej, której chcesz użyć. W wierszu polecenia Użyj jednej opcji **/NODEFAULTLIB** dla każdej biblioteki do ignorowania. W środowisku IDE programu Visual Studio oddziel biblioteki do ignorowania przez średnika w właściwości **Ignoruj określone biblioteki domyślne** .

| Aby użyć tej biblioteki wykonawczej | Ignoruj te biblioteki |
|-----------------------------------|----------------------------|
| Wielowątkowy (libcmt. lib) | msvcrt. lib; libcmtd. lib; msvcrtd. lib |
| Wielowątkowe używanie biblioteki DLL (msvcrt. lib) | libcmt. lib; libcmtd. lib; msvcrtd. lib |
| Debuguj wielowątkowe (libcmtd. lib) | libcmt. lib; msvcrt. lib; msvcrtd. lib |
| Debuguj wielowątkowość za pomocą biblioteki DLL (msvcrtd. lib) | libcmt. lib; msvcrt. lib; libcmtd. lib |

Na przykład, jeśli otrzymasz to ostrzeżenie i chcesz utworzyć plik wykonywalny, który używa niedebugowanej wersji biblioteki DLL bibliotek czasu wykonywania, można użyć następujących opcji z konsolidatorem:

```cmd
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```
