---
title: Zmienianie domyślnej fabryki klas i modelu agregacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 203aeae7dd2edb179ec3f9c1f56f989ffc09b35c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093015"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>Zmienianie domyślnej fabryki klas i modelu agregacji

Używa ATL [CComCoClass](../atl/reference/ccomcoclass-class.md) do definiowania domyślnej klasy fabryki i agregację modelu obiektu. `CComCoClass` Określa dwa następujące makra:

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) deklaruje fabryki klas jako [CComClassFactory](../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) deklaruje, że obiekt może być agregowany.

Można zastąpić jedną z tych wartości domyślnych, określając innego makra w definicji klasy. Na przykład, aby użyć [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) zamiast `CComClassFactory`, określ [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) makra:

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

Są dwa makra, które definiują fabrykę klas [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) i [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).

Używa również biblioteki ATL **typedef** mechanizmu, aby zaimplementować domyślne zachowanie. Na przykład używa makro DECLARE_AGGREGATABLE **typedef** definiowaniu typu o nazwie `_CreatorClass`, który jest następnie odwoływać w całym ATL. Należy pamiętać, że w klasie pochodnej **typedef** przy użyciu tej samej nazwie jako klasa bazowa **— typedef** skutkuje ATL za pomocą definicji i zastępowanie domyślnego zachowania.

## <a name="see-also"></a>Zobacz też

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Makra agregacji i fabryki klas](../atl/reference/aggregation-and-class-factory-macros.md)

