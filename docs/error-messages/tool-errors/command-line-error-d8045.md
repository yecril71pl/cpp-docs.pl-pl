---
title: Błąd D8045 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 7964c2539b5358d2d946e530c4ee75110857446d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490598"
---
# <a name="command-line-error-d8045"></a>Błąd D8045 wiersza polecenia

Nie można skompilować pliku C "file" z opcją/CLR

Tylko pliki źródłowe C++ kod może być przekazywany do kompilacji, który używa **/CLR**.  Użyj **/TP** skompilować plik .c, jako plik .cpp; zobacz [TP, /Tp-TP, /TP (Określ źródło pliku typu)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 wiersza polecenia może również wystąpić, jeśli kompilujesz aplikację ATL, przy użyciu języka Visual C++. Zobacz [porady: Migracja do/CLR](../../dotnet/how-to-migrate-to-clr.md) Aby uzyskać więcej informacji.