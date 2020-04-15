---
title: TemplateInstantiation, klasa
description: Odwołanie do klasy SDK TemplateInstantiation w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ba8fd10efc6a536c9160f10b19e19e17bfaaad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324220"
---
# <a name="templateinstantiation-class"></a>TemplateInstantiation, klasa

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Klasa `TemplateInstantiation` jest używana z funkcjami [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)i [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Użyj go, aby dopasować [zdarzenie TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

## <a name="syntax"></a>Składnia

```cpp
class TemplateInstantiation : public Activity
{
public:
    enum class Kind
    {
        CLASS       = TEMPLATE_INSTANTIATION_KIND_CODE_CLASS,
        FUNCTION    = TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION,
        VARIABLE    = TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE,
        CONCEPT     = TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT
    };

    TemplateInstantiation(const RawEvent& event);

    const unsigned long long& SpecializationSymbolKey() const;
    const unsigned long long& PrimaryTemplateSymbolKey() const;

    Kind Kind() const;
};
```

## <a name="members"></a>Elementy członkowskie

Wraz z odziedziczonych elementów członkowskich z `TemplateInstantiation` jego [działania](activity.md) klasy podstawowej, klasa zawiera następujące elementy członkowskie:

### <a name="constructors"></a>Konstruktorów

[SzablonInstantiation](#template-instantiation)

### <a name="functions"></a>Funkcje

[Rodzaj](#kind)
[PrimaryTemplateSymbolKey](#primary-template-symbol-key)
[SpecjalizacjeSymbolKey](#specialization-symbol-key)

## <a name="kind"></a><a name="kind"></a>Rodzaju

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>Wartość zwracana

Kod opisujący typ wystąpienia szablonu, który został wykonany.

## <a name="primarytemplatesymbolkey"></a><a name="primary-template-symbol-key"></a>PrimaryTemplateSymbolKey

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator numeryczny dla typu szablonu, który był wyspecjalizowany. Ten identyfikator jest unikatowy w ramach przebiegu front-end kompilatora.

## <a name="specializationsymbolkey"></a><a name="specialization-symbol-key"></a>SpecjalizacjeSymbolKey

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator numeryczny dla typu specjalizacji. Ten identyfikator jest unikatowy w ramach przebiegu front-end kompilatora.

## <a name="templateinstantiation"></a><a name="template-instantiation"></a>SzablonInstantiation

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Zdarzenie*\
Wydarzenie [TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

::: moniker-end
