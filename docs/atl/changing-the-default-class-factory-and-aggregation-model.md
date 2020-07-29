---
title: Zmiana domyślnej fabryki klas i modelu agregacji
ms.date: 11/04/2016
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
ms.openlocfilehash: 1c97d8f63a441fab2b76c6e0509e4b3f384308ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220889"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>Zmiana domyślnej fabryki klas i modelu agregacji

ATL używa [CComCoClass](../atl/reference/ccomcoclass-class.md) do definiowania domyślnego fabryki klas i modelu agregacji dla obiektu. `CComCoClass`Określa dwa następujące makra:

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) Deklaruje fabrykę klas do [CComClassFactory](../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) Deklaruje, że obiekt może być zagregowany.

Można zastąpić jedno z tych ustawień domyślnych, określając inne makro w definicji klasy. Na przykład, aby użyć [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) zamiast `CComClassFactory` , określ makro [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) :

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

Dwa inne makra definiujące fabrykę klasy są [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) i [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).

ATL używa również **`typedef`** mechanizmu do implementowania zachowania domyślnego. Na przykład makro DECLARE_AGGREGATABLE używa **`typedef`** do definiowania typu wywoływanego, do `_CreatorClass` którego odwołuje się w obrębie ATL. Należy zauważyć, że w klasie pochodnej, **`typedef`** przy użyciu takiej samej nazwy, jak wyniki klasy bazowej **`typedef`** w ATL przy użyciu definicji i zastępowanie zachowania domyślnego.

## <a name="see-also"></a>Zobacz także

[Podstawowe informacje o obiektach COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Makra agregacji i fabryki klas](../atl/reference/aggregation-and-class-factory-macros.md)
