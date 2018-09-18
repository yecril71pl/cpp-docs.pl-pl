---
title: Błąd PRJ0033 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c70bd942123c48866c3353443b478de4953668de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036075"
---
# <a name="project-build-error-prj0033"></a>Błąd PRJ0033 kompilacji projektu

Właściwość 'Dodatkowe zależności' dla kroku kompilacji niestandardowej krok dla pliku 'Plik' zawiera 'makra"co ewaluowane jest"macro_expansion".

Wystąpił błąd podczas jego dodatkowe zależności, prawdopodobnie z powodu problemu z oceny makra znajdujących się w niestandardowego kroku kompilacji dla pliku. Ten błąd może również oznaczać, że ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makra, lub usuń specyfikację ścieżki. Oceniono ścieżka jest ścieżką bezwzględną z katalogu projektu.