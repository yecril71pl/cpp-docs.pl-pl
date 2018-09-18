---
title: Błąd d8045 wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8045
dev_langs:
- C++
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6838202178e8012df61d17e2434461d6f4858bf3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022789"
---
# <a name="command-line-error-d8045"></a>Błąd D8045 wiersza polecenia

Nie można skompilować pliku C "file" z opcją/CLR

Tylko pliki źródłowe C++ kod może być przekazywany do kompilacji, który używa **/CLR**.  Użyj **/TP** skompilować plik .c, jako plik .cpp; zobacz [TP, /Tp-TP, /TP (Określ źródło pliku typu)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 wiersza polecenia może również wystąpić, jeśli kompilujesz aplikację ATL, przy użyciu języka Visual C++. Zobacz [porady: Migracja do/CLR](../../dotnet/how-to-migrate-to-clr.md) Aby uzyskać więcej informacji.