---
title: "Magazynowanie literałów ciągu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2a1a001899e46fbd8894b72f2c8cd806f1834b7e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="storage-of-string-literals"></a>Magazynowanie literałów ciągu
Znaki literału ciągu są przechowywane w kolejności, w lokalizacji pamięci ciągłej. Sekwencja specjalna (takich jak  **\\ \\**  lub  **\\"**) wewnątrz literału ciągu traktowana jako pojedynczy znak. Znak null (reprezentowane przez **\0** sekwencja unikowa) jest automatycznie dołączane do i oznacza koniec, każdy ciąg literału. (Dzieje się tak podczas [fazy tłumaczenia](../preprocessor/phases-of-translation.md) 7.) Należy pamiętać, że kompilator nie mogą być przechowywane w dwóch identycznych ciągów w dwóch różnych adresów. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) wymusza na umieszczenie pojedynczej kopii identycznych ciągów w pliku wykonywalnego.  
  
## <a name="remarks"></a>Uwagi  
 **Dotyczące firmy Microsoft**  
  
 Ciągi mieć statycznego okresu przechowywania. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) informacji o okresem magazynu.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Literały ciągu języka C](../c-language/c-string-literals.md)