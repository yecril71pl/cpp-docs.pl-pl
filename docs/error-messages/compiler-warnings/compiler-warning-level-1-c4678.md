---
title: Kompilator ostrzeżenie (poziom 1) C4678 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81eb7df618f97300c2654cc0f4f7a58d18215b26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076102"
---
# <a name="compiler-warning-level-1-c4678"></a>Kompilator ostrzeżenie (poziom 1) C4678

Klasa bazowa "base_type" jest mniej dostępny niż "derived_type"

Typ publiczny pochodzi od typu prywatnego. Typ publiczny jest tworzone wystąpienie w przywoływanym zestawie elementów członkowskich prywatnych typu podstawowego nie będzie dostępny.

C4678 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**. Jest to błąd, korzystając z **/CLR**, aby mieć klasę bazową, która jest mniej dostępny, jego klasy pochodnej.
