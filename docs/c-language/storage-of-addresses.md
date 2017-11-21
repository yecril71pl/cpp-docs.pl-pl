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
ms.openlocfilehash: 3d0e996ac191ba3091925a85937e7636a2425215
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="storage-of-addresses"></a>Magazynowanie adresów
Ilości miejsca wymaganego dla adresu i znaczenie adresu są zależne od implementacji kompilatora. Wskaźniki do różnych typów nie ma gwarancji ma taką samą długość. W związku z tym **sizeof (char \*)** nie jest zawsze równa **sizeof (int \*)**.  
  
 **Dotyczące firmy Microsoft**  
  
 Dla kompilatora Microsoft C **sizeof (char \*)** jest równa **sizeof (int \*)**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje wskaźników](../c-language/pointer-declarations.md)