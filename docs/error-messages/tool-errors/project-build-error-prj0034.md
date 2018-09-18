---
title: Błąd PRJ0034 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0034
dev_langs:
- C++
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b271875173bf0e55d94989d60a1c8f7aaf408b2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065585"
---
# <a name="project-build-error-prj0034"></a>Błąd PRJ0034 kompilacji projektu

Właściwość 'Dodatkowe zależności' dla niestandardowego na poziomie projektu kompilacji kroku zawarte "makra" ewaluowane jest jako "macro_expansion".

Wystąpił błąd podczas jego dodatkowe zależności, prawdopodobnie z powodu problemu z oceny makra znajdujących się w niestandardowego kroku kompilacji dla projektu. Ten błąd może również oznaczać, że ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makra, lub usuń specyfikację ścieżki. Oceniono ścieżka jest ścieżką bezwzględną z katalogu projektu.