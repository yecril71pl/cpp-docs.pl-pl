---
title: Bloki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9704b499106fc59364f5cc9ae97277939e835a77
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025325"
---
# <a name="blocks"></a>Bloki

Sekwencja deklaracje, definicje i instrukcji ujętych w nawiasy klamrowe (**{}**) nosi nazwę "zablokowanie". Istnieją dwa typy bloków w C. "Instrukcja złożona," oświadczenia składa się z jednego lub więcej instrukcji (zobacz [instrukcji złożonej](../c-language/compound-statement-c.md)), jest jednym z typów bloku. Druga, "Definicja funkcji", składa się z instrukcji złożonej (treści funkcji), a także funkcja skojarzonej "header" (nazwa funkcji, zwracany typ i parametry formalne). Blok, w ramach innych bloków jest nazywany jest "nested."

Należy pamiętać, że gdy wszystkie instrukcje złożone są ujęte w nawiasy klamrowe, nie wszystkie czynności, ujęte w nawiasy klamrowe stanowi instrukcję złożonego. Na przykład specyfikacje elementów tablicy, struktury lub wyliczenie może znajdować się w obrębie nawiasów klamrowych, nie są one instrukcje złożone.

## <a name="see-also"></a>Zobacz też

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)