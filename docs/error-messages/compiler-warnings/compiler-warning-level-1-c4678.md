---
title: Kompilator ostrzeżenie (poziom 1) C4678
ms.date: 11/04/2016
f1_keywords:
- C4678
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
ms.openlocfilehash: 9e61d919f08bbbf4f3e74da7ba4f2388516d3152
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374524"
---
# <a name="compiler-warning-level-1-c4678"></a>Kompilator ostrzeżenie (poziom 1) C4678

Klasa bazowa "base_type" jest mniej dostępny niż "derived_type"

Typ publiczny pochodzi od typu prywatnego. Typ publiczny jest tworzone wystąpienie w przywoływanym zestawie elementów członkowskich prywatnych typu podstawowego nie będzie dostępny.

C4678 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**. Jest to błąd, korzystając z **/CLR**, aby mieć klasę bazową, która jest mniej dostępny, jego klasy pochodnej.
