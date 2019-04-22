---
title: Kompilator ostrzeżenie (poziom 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: f73fa8e09baab127e7755ebe3def69c2fb585744
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028470"
---
# <a name="compiler-warning-level-1-c4274"></a>Kompilator ostrzeżenie (poziom 1) C4274

\#Ident ignorowane. zobacz dokumentację dla #pragma comment (exestr, "string")

`#ident` Dyrektywy, który wstawia ciągiem zdefiniowanym przez użytkownika w obiekcie lub plik wykonywalny jest przestarzały. W związku z tym Kompilator ignoruje dyrektywy.

> [!CAUTION]
>  C4274 ostrzeżenie z informacją o tym przy użyciu [#pragma comment (exestr, "string")](../../preprocessor/comment-c-cpp.md) dyrektywy. Jednak ta informacja jest przestarzały i zostanie zaktualizowany w przyszłej wersji kompilatora. Jeśli używasz `#pragma` dyrektywy, narzędzie program łączący (LINK.exe) ignoruje rekordu komentarz produkowane przez dyrektywę i ostrzeżenie [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Zamiast `#ident` dyrektywy, firma Microsoft zaleca użycie ciąg zasobu wersji pliku w aplikacji.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń `#ident "` *ciąg* `"` dyrektywy.

## <a name="see-also"></a>Zobacz także

[komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Ostrzeżenie narzędzi konsolidatora LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Praca z plikami zasobów](../../windows/working-with-resource-files.md)