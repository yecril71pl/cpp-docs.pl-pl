---
title: Naked (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 474cb57ced17088c0ce9be8613a9373c702afe69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="naked-c"></a>Naked (C)
**Dotyczące firmy Microsoft**  
  
 Atrybut naked klasy magazynu to rozszerzenie specyficzne dla firmy Microsoft dla języka C. Kompilator generuje kod bez prologu i epilogu zadeklarowana z atrybutem naked Klasa magazynu funkcji. Gołe funkcje są przydatne, gdy trzeba napisać własne sekwencje kodu prologu/epilogu przy użyciu kodu wbudowanego asemblera. Gołe funkcje są przydatne do zapisywania sterowniki urządzeń wirtualnych.  
  
 Aby uzyskać szczegółowe informacje o użyciu naked atrybutu, zobacz [funkcji Naked](../c-language/naked-functions.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzone atrybuty klasy magazynu języka C](../c-language/c-extended-storage-class-attributes.md)