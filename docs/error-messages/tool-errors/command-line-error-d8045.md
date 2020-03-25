---
title: Błąd D8045 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 05a2d3851e58062e1e326781a223e2f4b0346620
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196849"
---
# <a name="command-line-error-d8045"></a>Błąd D8045 wiersza polecenia

nie można skompilować pliku C "File" z opcją/CLR

Tylko C++ pliki kodu źródłowego można przesłać do kompilacji korzystającej z **/CLR**.  Użyj **/TP** , aby skompilować plik. c jako plik. cpp; Aby uzyskać więcej informacji [, zobacz/TC,/TP,/TC,/TP (Określ typ pliku źródłowego)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) .

Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 wiersza polecenia może również wystąpić w przypadku kompilowania aplikacji ATL przy użyciu C++wizualizacji. Aby uzyskać więcej informacji [, zobacz How to: Migruj do/CLR](../../dotnet/how-to-migrate-to-clr.md) .
