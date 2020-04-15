---
title: Ostrzeżenie kompilatora (poziom 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5d005fccc5920aea61698a65edf9284d56366a1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377074"
---
# <a name="compiler-warning-level-1-c4274"></a>Ostrzeżenie kompilatora (poziom 1) C4274

\#ident ignorowane; zobacz dokumentację #pragma comment(exestr, 'string')

Dyrektywa, `#ident` która wstawia ciąg określony przez użytkownika do obiektu lub pliku wykonywalnego, jest przestarzała. W związku z tym kompilator ignoruje dyrektywy.

> [!CAUTION]
> Ostrzeżenie C4274 zaleca użycie [dyrektywy #pragma comment(exestr, 'string".](../../preprocessor/comment-c-cpp.md) Jednak ta rada jest przestarzała i zostaną zmienione w przyszłej wersji kompilatora. Jeśli używasz `#pragma` dyrektywy, narzędzie konsolidatora (LINK.exe) ignoruje rekord komentarza wyprodukowany przez dyrektywę i wydaje ostrzeżenie [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Zamiast `#ident` dyrektywy zaleca się użycie ciągu zasobu wersji pliku w aplikacji.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń `#ident "`dyrektywę *ciągu.* `"`

## <a name="see-also"></a>Zobacz też

[komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Ostrzeżenie o narzędziach konsolidatora LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Praca z plikami zasobów](../../windows/working-with-resource-files.md)
