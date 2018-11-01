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
ms.openlocfilehash: 061cc04857b0d1763fb4ee975912bcca1b9d014f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455279"
---
# <a name="accessing-run-time-class-information"></a>Uzyskiwanie dostępu do informacji o klasie czasu wykonywania

W tym artykule wyjaśniono, jak uzyskać dostęp do informacji o klasie obiektu w czasie wykonywania.

> [!NOTE]
>  Nie używa MFC [informacje typu Run-Time](../cpp/run-time-type-information.md) pomocy technicznej (RTTI) wprowadzone w programie Visual C++ 4.0.

Jeśli mają pochodne klasy z [CObject](../mfc/reference/cobject-class.md) i używać **DECLARE**_**dynamiczne** i `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` i `IMPLEMENT_DYNCREATE`, lub `DECLARE_SERIAL` i `IMPLEMENT_SERIAL` makra opisane w artykule [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md), `CObject` klasa ma możliwość określenia dokładnego klasę obiektu w czasie wykonywania.

Ta możliwość jest najbardziej użyteczna, gdy są potrzebne dodatkowe sprawdzanie argumenty funkcji typu i kiedy należy napisać kod specjalnych, na podstawie klasy obiektu. Jednak takie rozwiązanie jest zwykle niezalecane, ponieważ że duplikuje funkcje funkcje wirtualne.

`CObject` Funkcja elementu członkowskiego `IsKindOf` może służyć do ustalenia, czy określony obiekt należy do określonej klasy, lub jeśli pochodzi z określonej klasy. Argument `IsKindOf` jest `CRuntimeClass` obiektu, który można uzyskać za pomocą `RUNTIME_CLASS` — makro o nazwie klasy.

### <a name="to-use-the-runtimeclass-macro"></a>Aby użyć makra RUNTIME_CLASS

1. Użyj `RUNTIME_CLASS` o nazwie klasy, jak pokazano poniżej, dla klasy `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Należy rzadko bezpośredni dostęp do obiektu klasy środowiska wykonawczego. Częściej spotykanym sposobem wykorzystania jest przekazanie obiektu klasy środowiska wykonawczego, aby `IsKindOf` funkcji, jak pokazano w następnej procedurze. `IsKindOf` Funkcja sprawdza obiekt, aby zobaczyć, czy należy on do określonej klasy.

#### <a name="to-use-the-iskindof-function"></a>Aby użyć funkcji IsKindOf

1. Upewnij się, że klasa ma pomocy technicznej w klasie czasu wykonywania. Oznacza to, że klasa musi otrzymano bezpośrednio lub pośrednio ze `CObject` i używać **DECLARE**_**dynamiczne** i `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` i `IMPLEMENT_DYNCREATE`, lub `DECLARE_SERIAL` i `IMPLEMENT_SERIAL` makra opisane w artykule [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md).

1. Wywołaj `IsKindOf` funkcja elementu członkowskiego dla obiektów tej klasy przy użyciu `RUNTIME_CLASS` makra, aby wygenerować `CRuntimeClass` argumentu, jak pokazano poniżej:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  Zwraca IsKindOf **TRUE** Jeśli obiekt jest członkiem określonej klasy lub klasy pochodzącej od określonej klasy. `IsKindOf` nie obsługuje wielu dziedziczenie lub wirtualne klasy bazowe, chociaż używają wielokrotnego dziedziczenia z klas pochodnych Microsoft Foundation w razie potrzeby.

Dynamiczne tworzenie obiektów jest jedno użycie informacji o klasie czasu wykonywania. Ten proces został omówiony w artykule [dynamiczne tworzenie obiektów](../mfc/dynamic-object-creation.md).

Aby uzyskać szczegółowe informacje o serializacji i informacje o klasie czasu wykonywania, zobacz artykuły [pliki w MFC](../mfc/files-in-mfc.md) i [serializacji](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Używanie obiektu CObject](../mfc/using-cobject.md)

