---
title: "Magazynowanie adresów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd82f6f5046cf910fbc871be37d4af5856796792
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-addresses"></a>Magazynowanie adresów
Ilości miejsca wymaganego dla adresu i znaczenie adresu są zależne od implementacji kompilatora. Wskaźniki do różnych typów nie ma gwarancji ma taką samą długość. W związku z tym **sizeof (char \*)** nie jest zawsze równa **sizeof (int \*)**.  
  
 **Dotyczące firmy Microsoft**  
  
 Dla kompilatora Microsoft C **sizeof (char \*)** jest równa **sizeof (int \*)**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje wskaźników](../c-language/pointer-declarations.md)