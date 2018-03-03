---
title: "Kompilatora (poziom 1) ostrzeżenie C4678 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7648101a0862aa2006feff73a5ebe32bd0f424a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4678"></a>Kompilator C4678 ostrzegawcze (poziom 1)
Klasa podstawowa "base_type" jest mniej dostępny niż "derived_type"  
  
Publiczny typ pochodzi z typu prywatne. Jeśli wystąpienia typu publicznego w przywoływanym zestawie członków prywatnych typu podstawowego nie będą dostępne.  
  
C4678 jest tylko przy użyciu opcji kompilatora przestarzałe **: oldsyntax**. Jest to błąd, używając **/CLR**, aby mieć klasy podstawowej, która jest mniej dostępny który jego klasy pochodnej.  
