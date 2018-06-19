---
title: Magazynowanie literałów ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d87998f7e9d579c012f5db2f38f20886c1e74c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387037"
---
# <a name="storage-of-string-literals"></a>Magazynowanie literałów ciągu
Znaki literału ciągu są przechowywane w kolejności, w lokalizacji pamięci ciągłej. Sekwencja specjalna (takich jak **\\ \\** lub  **\\"**) wewnątrz literału ciągu traktowana jako pojedynczy znak. Znak null (reprezentowane przez **\0** sekwencja unikowa) jest automatycznie dołączane do i oznacza koniec, każdy ciąg literału. (Dzieje się tak podczas [fazy tłumaczenia](../preprocessor/phases-of-translation.md) 7.) Należy pamiętać, że kompilator nie mogą być przechowywane w dwóch identycznych ciągów w dwóch różnych adresów. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) wymusza na umieszczenie pojedynczej kopii identycznych ciągów w pliku wykonywalnego.  
  
## <a name="remarks"></a>Uwagi  
 **Microsoft Specific**  
  
 Ciągi mieć statycznego okresu przechowywania. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) informacji o okresem magazynu.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Literały ciągu języka C](../c-language/c-string-literals.md)