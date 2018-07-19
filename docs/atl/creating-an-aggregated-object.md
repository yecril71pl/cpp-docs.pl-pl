---
title: Tworzenie obiektu zagregowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f6ff5a0fdcff62d62469f17388f633b83739a09
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850829"
---
# <a name="creating-an-aggregated-object"></a>Tworzenie obiektu zagregowanego
Delegaty agregacji `IUnknown` wywołań, podając wskaźnik do obiektu zewnętrznego `IUnknown` do obiektu wewnętrznego.  
  
### <a name="to-create-an-aggregated-object"></a>Do utworzenia obiektu zagregowanego  
  
1.  Dodaj `IUnknown` wskaźnik do klasy obiektu i zainicjować go na wartość NULL w konstruktorze.  
  
2.  Zastąp [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) do utworzenia agregacji.  
  
3.  Użyj `IUnknown` wskaźnika, zdefiniowane w kroku 1, jako drugi parametr dla [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) makra.  
  
4.  Zastąp [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) zwolnić `IUnknown` wskaźnika.  
  
> [!NOTE]
>  Jeśli używasz i zwolnij interfejs z obiektu zagregowanego podczas `FinalConstruct`, należy dodać [DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) makra do definicji obiektu klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)

