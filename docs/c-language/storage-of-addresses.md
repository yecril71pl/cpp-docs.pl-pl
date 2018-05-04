---
title: Magazynowanie adresów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d892aac81efa8c2628c8662558b52cc1eb2e21c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="storage-of-addresses"></a>Magazynowanie adresów
Ilości miejsca wymaganego dla adresu i znaczenie adresu są zależne od implementacji kompilatora. Wskaźniki do różnych typów nie ma gwarancji ma taką samą długość. W związku z tym **sizeof (char \*)** nie jest zawsze równa **sizeof (int \*)**.  
  
 **Microsoft Specific**  
  
 Dla kompilatora Microsoft C **sizeof (char \*)** jest równa **sizeof (int \*)**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje wskaźników](../c-language/pointer-declarations.md)