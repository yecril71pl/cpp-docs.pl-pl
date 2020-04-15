---
title: Uzyskiwanie dostępu do informacji o klasie czasu wykonywania
ms.date: 11/04/2016
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
ms.openlocfilehash: 4a836bb7bd03bd6654e5c940442fecf541042fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354223"
---
# <a name="accessing-run-time-class-information"></a>Uzyskiwanie dostępu do informacji o klasie czasu wykonywania

W tym artykule wyjaśniono, jak uzyskać dostęp do informacji o klasie obiektu w czasie wykonywania.

> [!NOTE]
> MFC nie korzysta z pomocy technicznej [informacji o typie czasu wykonywania](../cpp/run-time-type-information.md) (RTTI) wprowadzonej w programie Visual C++ 4.0.

Jeśli klasa pochodzi od [CObject](../mfc/reference/cobject-class.md) i używane **DECLARE** `IMPLEMENT_DYNAMIC`_ `DECLARE_DYNCREATE` **DYNAMIC** i , `IMPLEMENT_SERIAL` i `IMPLEMENT_DYNCREATE`, lub `DECLARE_SERIAL` i makra wyjaśnione w artykule [Pochodne klasy z CObject](../mfc/deriving-a-class-from-cobject.md), `CObject` klasa ma możliwość określenia dokładnej klasy obiektu w czasie wykonywania.

Ta możliwość jest najbardziej przydatna, gdy potrzebne jest sprawdzanie dodatkowych typów argumentów funkcji i gdy należy napisać kod specjalnego przeznaczenia na podstawie klasy obiektu. Jednak ta praktyka nie jest zwykle zalecane, ponieważ powiela funkcjonalność funkcji wirtualnych.

Funkcja `CObject` `IsKindOf` elementu członkowskiego może służyć do określenia, czy określony obiekt należy do określonej klasy lub jeśli pochodzi od określonej klasy. Argument `IsKindOf` jest obiektem, `CRuntimeClass` który można uzyskać `RUNTIME_CLASS` przy użyciu makra o nazwie klasy.

### <a name="to-use-the-runtime_class-macro"></a>Aby użyć makra RUNTIME_CLASS

1. Użyj `RUNTIME_CLASS` z nazwą klasy, jak pokazano w `CObject`tym miejscu dla klasy:

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Rzadko trzeba będzie uzyskać dostęp do obiektu klasy w czasie wykonywania bezpośrednio. Bardziej typowym zastosowaniem jest przekazanie obiektu klasy `IsKindOf` wykonywania do funkcji, jak pokazano w następnej procedurze. Funkcja `IsKindOf` testuje obiekt, aby sprawdzić, czy należy do określonej klasy.

#### <a name="to-use-the-iskindof-function"></a>Aby użyć funkcji IsKindOf

1. Upewnij się, że klasa ma wsparcie klasy run-time. Oznacza to, że klasa musi być pochodną `CObject` bezpośrednio lub pośrednio `IMPLEMENT_DYNAMIC`z `DECLARE_DYNCREATE` **declare**_ `DECLARE_SERIAL` **DYNAMIC** i , `IMPLEMENT_DYNCREATE`i , lub i `IMPLEMENT_SERIAL` makra wyjaśnione w artykule [Pochodne klasy z CObject](../mfc/deriving-a-class-from-cobject.md).

1. Wywołanie `IsKindOf` funkcji elementu członkowskiego dla obiektów `RUNTIME_CLASS` tej klasy, używając makra do wygenerowania argumentu, `CRuntimeClass` jak pokazano poniżej:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf zwraca **wartość PRAWDA,** jeśli obiekt jest członkiem określonej klasy lub klasy pochodnej określonej klasy. `IsKindOf`nie obsługuje wielu dziedziczenia lub wirtualnych klas podstawowych, chociaż można użyć wielu dziedziczenia dla pochodnych klas programu Microsoft Foundation, jeśli to konieczne.

Jednym z zastosowań informacji o klasie wykonywania jest dynamiczne tworzenie obiektów. Ten proces został omówiony w artykule [Dynamiczne tworzenie obiektów](../mfc/dynamic-object-creation.md).

Aby uzyskać bardziej szczegółowe informacje na temat serializacji i informacji o klasach w czasie wykonywania, zobacz artykuły [Pliki w MFC](../mfc/files-in-mfc.md) i [Serializacji](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Używanie obiektu CObject](../mfc/using-cobject.md)
