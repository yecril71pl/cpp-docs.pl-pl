---
title: Tworzenie obiektu zagregowanego
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
ms.openlocfilehash: 4be8d0e852da91b58125dc01d44eed4560b2b8d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277524"
---
# <a name="creating-an-aggregated-object"></a>Tworzenie obiektu zagregowanego

Delegaty agregacji `IUnknown` wywołań, podając wskaźnik do obiektu zewnętrznego `IUnknown` do obiektu wewnętrznego.

## <a name="to-create-an-aggregated-object"></a>Do utworzenia obiektu zagregowanego

1. Dodaj `IUnknown` wskaźnik do klasy obiektu i zainicjować go na wartość NULL w konstruktorze.

1. Zastąp [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) do utworzenia agregacji.

1. Użyj `IUnknown` wskaźnika, zdefiniowane w kroku 1, jako drugi parametr dla [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) makra.

1. Zastąp [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) zwolnić `IUnknown` wskaźnika.

> [!NOTE]
> Jeśli używasz i zwolnij interfejs z obiektu zagregowanego podczas `FinalConstruct`, należy dodać [DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) makra do definicji obiektu klasy.

## <a name="see-also"></a>Zobacz także

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)
