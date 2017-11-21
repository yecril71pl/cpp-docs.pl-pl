---
title: "Kompilatora (poziom 1) ostrzeżenie C4678 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4678
dev_langs: C++
helpviewer_keywords: C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 52ebd41531cd5fdfd7aeb6ba6f52cf8981fa6120
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4678"></a>Kompilator C4678 ostrzegawcze (poziom 1)
Klasa podstawowa "base_type" jest mniej dostępny niż "derived_type"  
  
Publiczny typ pochodzi z typu prywatne. Jeśli wystąpienia typu publicznego w przywoływanym zestawie członków prywatnych typu podstawowego nie będą dostępne.  
  
C4678 jest tylko przy użyciu opcji kompilatora przestarzałe **: oldsyntax**. Jest to błąd, używając **/CLR**, aby mieć klasy podstawowej, która jest mniej dostępny który jego klasy pochodnej.  
