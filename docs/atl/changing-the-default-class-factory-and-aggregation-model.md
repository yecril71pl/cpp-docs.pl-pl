---
title: "Zmiana domyślnego fabryki klasy i modelu agregacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a963c1fba2d3eda9c86fa1e6db74de739bf45182
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>Zmiana domyślnego fabryki klasy i modelu agregacji
ATL używa [klasy CComCoClass](../atl/reference/ccomcoclass-class.md) do definiowania domyślnej klasy fabryki i agregację modelu dla obiektu. `CComCoClass`Określa dwa następujące makra:  
  
-   [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) deklaruje fabryki klasy jako [CComClassFactory](../atl/reference/ccomclassfactory-class.md).  
  
-   [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) deklaruje zagregowane obiektu.  
  
 Można zastąpić jedną z tych wartości domyślnych, określając innego makra w definicji klasy. Na przykład, aby użyć [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) zamiast `CComClassFactory`, określ [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) makra:  
  
 [!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]  
  
 Są dwa makra, które definiują fabrykę klas [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) i [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).  
  
 ATL używa również `typedef` mechanizm do zaimplementowania zachowanie domyślne. Na przykład `DECLARE_AGGREGATABLE` korzysta z makra `typedef` do definiowania typu o nazwie **_CreatorClass**, który następnie jest przywoływany przez ATL. Należy pamiętać, że w klasie pochodnej `typedef` przy użyciu takiej samej nazwie jako klasa podstawowa `typedef` powoduje ATL za pomocą definicję i zastępowanie domyślnego zachowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat ATL COM — obiekty](../atl/fundamentals-of-atl-com-objects.md)   
 [Agregacja i makra fabryki klas](../atl/reference/aggregation-and-class-factory-macros.md)

