---
title: Tworzenie obiektu zagregowane | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b6b66a80c5459157b644ec6b264b707232c83e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-aggregated-object"></a>Tworzenie obiektu zagregowane
Obiekty delegowane agregacji **IUnknown** wywołań, zapewniając wskaźnik do obiektu zewnętrznego **IUnknown** do obiektu wewnętrznego.  
  
### <a name="to-create-an-aggregated-object"></a>Aby utworzyć obiekt zagregowane  
  
1.  Dodaj **IUnknown** wskaźnika do klasy i zainicjować go do **NULL** w konstruktorze.  
  
2.  Zastąpienie [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) można utworzyć agregacji.  
  
3.  Użyj **IUnknown** wskaźnika, zdefiniowane w kroku 1 jako drugiego parametru dla [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) makra.  
  
4.  Zastąpienie [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) zwolnienia **IUnknown** wskaźnika.  
  
> [!NOTE]
>  Jeśli używane i wersji interfejsu z zagregowane obiektu podczas `FinalConstruct`, należy dodać [DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) makra w definicji klasy obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)

