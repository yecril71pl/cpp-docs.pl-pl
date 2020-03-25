---
title: Ostrzeżenie kompilatora (poziom 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5f2350f275f883e7bf18aa1621d08b34132e8dfb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175849"
---
# <a name="compiler-warning-level-1-c4274"></a>Ostrzeżenie kompilatora (poziom 1) C4274

Zignorowano \#ident; Zapoznaj się z dokumentacją #pragma comment (exestr, "String")

Dyrektywa `#ident`, która wstawia określony przez użytkownika ciąg w obiekcie lub pliku wykonywalnym, jest przestarzała. W związku z tym kompilator ignoruje dyrektywę.

> [!CAUTION]
>  Ostrzeżenie C4274 zaleca #pragma użycie dyrektywy [comment (exestr, "String")](../../preprocessor/comment-c-cpp.md) . Jednakże to zalecenie jest przestarzałe i zostanie zmienione w przyszłych wydaniach kompilatora. Jeśli używasz dyrektywy `#pragma`, narzędzie konsolidatora (LINK. exe) zignoruje rekord komentarza utworzony przez dyrektywę i wygeneruje ostrzeżenie [lnk4229 narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Zamiast dyrektywy `#ident` zalecamy użycie w aplikacji ciągu zasobu w wersji pliku.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń dyrektywę `#ident "`*string*`"`.

## <a name="see-also"></a>Zobacz też

[komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Ostrzeżenie narzędzi konsolidatora LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Praca z plikami zasobów](../../windows/working-with-resource-files.md)
