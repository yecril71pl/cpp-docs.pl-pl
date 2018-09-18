---
title: Kompilator ostrzeżenie (poziom 1) C4274 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4274
dev_langs:
- C++
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f6db0ee96674beda51ab02c8651e6f4960a0bf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094692"
---
# <a name="compiler-warning-level-1-c4274"></a>Kompilator ostrzeżenie (poziom 1) C4274

\#Ident ignorowane. zobacz dokumentację dla #pragma comment (exestr, "string")

`#ident` Dyrektywy, który wstawia ciągiem zdefiniowanym przez użytkownika w obiekcie lub plik wykonywalny jest przestarzały. W związku z tym Kompilator ignoruje dyrektywy.

> [!CAUTION]
>  C4274 ostrzeżenie z informacją o tym przy użyciu [#pragma comment (exestr, "string")](../../preprocessor/comment-c-cpp.md) dyrektywy. Jednak ta informacja jest przestarzały i zostanie zaktualizowany w przyszłej wersji kompilatora. Jeśli używasz `#pragma` dyrektywy, narzędzie program łączący (LINK.exe) ignoruje rekordu komentarz produkowane przez dyrektywę i ostrzeżenie [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Zamiast `#ident` dyrektywy, firma Microsoft zaleca użycie ciąg zasobu wersji pliku w aplikacji.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń `#ident "` *ciąg* `"` dyrektywy.

## <a name="see-also"></a>Zobacz też

[komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Ostrzeżenie narzędzi konsolidatora LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Praca z plikami zasobów](../../windows/working-with-resource-files.md)