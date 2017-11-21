---
title: "Uzyskiwanie dostępu do informacji o klasie czasu wykonywania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5cdc520118c0d50590927a88de816a593ea5e146
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="accessing-run-time-class-information"></a>Uzyskiwanie dostępu do informacji o klasie czasu wykonywania
W tym artykule wyjaśniono, jak uzyskać dostęp do informacji o klasie obiektu w czasie wykonywania.  
  
> [!NOTE]
>  MFC nie używa [informacje typu Run-Time](../cpp/run-time-type-information.md) pomocy technicznej (RTTI) wprowadzone w programie Visual C++ 4.0.  
  
 Jeśli ma pochodzi z klasy [CObject](../mfc/reference/cobject-class.md) i używać **DECLARE**_**dynamiczne** i `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` i `IMPLEMENT_DYNCREATE`, lub `DECLARE_SERIAL` i `IMPLEMENT_SERIAL` makra wyjaśniono w artykule [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md), `CObject` klasa ma możliwość określenia dokładnej klasy obiektu w czasie wykonywania.  
  
 Ta możliwość jest najbardziej przydatne, gdy wymagany jest typ dodatkowe sprawdzanie argumentów funkcji i należy napisać kod specjalnych oparty na klasie obiektu. Jednak takie rozwiązanie jest zwykle niezalecane, ponieważ jego duplikaty funkcji funkcji wirtualnych.  
  
 `CObject` Funkcji członkowskiej `IsKindOf` może służyć do określenia, czy dany obiekt należy do określonej klasy i jeśli pochodzi z określonej klasy. Argument `IsKindOf` jest `CRuntimeClass` obiektu, który można uzyskać za pomocą `RUNTIME_CLASS` makra o nazwie klasy.  
  
### <a name="to-use-the-runtimeclass-macro"></a>Aby użyć runtime_class — makro  
  
1.  Użyj `RUNTIME_CLASS` o nazwie klasy, jak pokazano poniżej klasy `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]  
  
 Rzadko należy bezpośrednio uzyskać dostęp do obiektu klasie czasu wykonywania. Najczęściej używana jest przekazanie obiektu klasie czasu wykonywania `IsKindOf` funkcji, jak pokazano w następnej procedurze. `IsKindOf` Funkcja testów obiekt, aby zobaczyć, czy należy do określonej klasy.  
  
#### <a name="to-use-the-iskindof-function"></a>Aby użyć tej funkcji IsKindOf  
  
1.  Upewnij się, że klasa obsługuje klasie czasu wykonywania. Oznacza to, że klasa musi zostały uzyskane bezpośrednio lub pośrednio z `CObject` i używać **DECLARE**_**dynamiczne** i `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` i `IMPLEMENT_DYNCREATE`, lub `DECLARE_SERIAL` i `IMPLEMENT_SERIAL` makra wyjaśniono w artykule [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md).  
  
2.  Wywołanie `IsKindOf` funkcji członkowskiej dla tej klasy obiektów przy użyciu `RUNTIME_CLASS` makro do generowania `CRuntimeClass` argumentu, jak pokazano poniżej:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]  
  
     [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]  
  
    > [!NOTE]
    >  Zwraca IsKindOf **TRUE** Jeśli obiekt jest członkiem określonej klasy lub klasę pochodzącą od określonej klasy. `IsKindOf`nie obsługuje wielu dziedziczenia lub wirtualne klasy podstawowe, chociaż można używać wielokrotne dziedziczenie z klas pochodnych Microsoft Foundation, w razie potrzeby.  
  
 Jedno użycie informacji o klasie czasu wykonywania jest dynamiczne tworzenie obiektów. Ten proces opisanej w artykule [dynamiczne tworzenie obiektów](../mfc/dynamic-object-creation.md).  
  
 Aby uzyskać szczegółowe informacje o serializacji i informacje o klasie czasu wykonywania, zobacz artykuły [pliki w MFC](../mfc/files-in-mfc.md) i [szeregowanie](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie obiektu CObject](../mfc/using-cobject.md)

