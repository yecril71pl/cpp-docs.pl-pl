---
title: TemplateInstantiationGroup, klasa
description: Odwołanie do klasy SDK SDK kompilacji języka C++.The C++ Build Insights SDK TemplateInstantiationGroup class reference.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 18dd48219c7c68ce152c381eb505fe37b19ec8dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324257"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup, klasa

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `TemplateInstantiationGroup` jest używana z [funkcjami MatchEventStack](../functions/match-event-stack.md) i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować grupy [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) zdarzeń.

## <a name="syntax"></a>Składnia

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych członków z [jego EventGroup\<TemplateInstantiation\> ](event-group.md) klasy podstawowej, `TemplateInstantiationGroup` klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[Grupa szablonów](#template-instantiation-group)

## <a name="templateinstantiationgroup"></a><a name="template-instantiation-group"></a>Grupa szablonów

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Parametry

*Grupa*\
Grupa [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) wydarzeń.

::: moniker-end
