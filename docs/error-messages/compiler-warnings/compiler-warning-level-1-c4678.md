---
title: Kompilatora (poziom 1) ostrzeżenie C4678 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 73871d69198752e12a629d441982c2da47146517
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284241"
---
# <a name="compiler-warning-level-1-c4678"></a>Kompilator C4678 ostrzegawcze (poziom 1)
Klasa podstawowa "base_type" jest mniej dostępny niż "derived_type"  
  
Publiczny typ pochodzi z typu prywatne. Jeśli wystąpienia typu publicznego w przywoływanym zestawie członków prywatnych typu podstawowego nie będą dostępne.  
  
C4678 jest tylko przy użyciu opcji kompilatora przestarzałe **: oldsyntax**. Jest to błąd, używając **/CLR**, aby mieć klasy podstawowej, która jest mniej dostępny który jego klasy pochodnej.  
