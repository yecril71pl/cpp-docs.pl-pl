---
title: Błąd PRJ0031 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0031
dev_langs:
- C++
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce97e8f540295f5a2968fce22312b8e0e34cfd2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076895"
---
# <a name="project-build-error-prj0031"></a>Błąd PRJ0031 kompilacji projektu

Właściwość 'Wyniki' dla kroku kompilacji niestandardowej krok dla pliku 'Plik' zawiera 'makra"co ewaluowane jest"macro_expansion".

Niestandardowego kroku kompilacji dla pliku miał złe dane wyjściowe, prawdopodobnie z powodu problemu z oceny makra. Ten błąd może również oznaczać, że ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makra, lub usuń specyfikację ścieżki. Oceniono ścieżka jest ścieżką bezwzględną z katalogu projektu.