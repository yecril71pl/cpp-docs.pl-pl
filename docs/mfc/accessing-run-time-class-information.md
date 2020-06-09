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
ms.openlocfilehash: a9f90640007f84c854d59cc27e0c38459c76fe46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619199"
---
# <a name="accessing-run-time-class-information"></a>Uzyskiwanie dostępu do informacji o klasie czasu wykonywania

W tym artykule wyjaśniono, jak uzyskać dostęp do informacji o klasie obiektu w czasie wykonywania.

> [!NOTE]
> MFC nie używa obsługi [informacji o typie czasu wykonywania](../cpp/run-time-type-information.md) (RTTI) wprowadzonej w Visual C++ 4,0.

Jeśli klasa pochodzi od [CObject](reference/cobject-class.md) i użyta zostanie **Deklaracja**$ _**Dynamic** i `IMPLEMENT_DYNAMIC` , `DECLARE_DYNCREATE` and `IMPLEMENT_DYNCREATE` lub, lub `DECLARE_SERIAL` i i i, lub i i i, lub i i i i, lub i i i `IMPLEMENT_SERIAL` [Deriving a Class from CObject](deriving-a-class-from-cobject.md) `CObject` .

Ta możliwość jest najbardziej przydatna, gdy jest potrzebne dodatkowe sprawdzanie typu argumentów funkcji, a kiedy trzeba pisać kod specjalnego przeznaczenia na podstawie klasy obiektu. Jednakże takie rozwiązanie nie jest zazwyczaj zalecane, ponieważ duplikuje funkcjonalność funkcji wirtualnych.

`CObject`Funkcja członkowska `IsKindOf` może służyć do określenia, czy określony obiekt należy do określonej klasy, czy też pochodzi od konkretnej klasy. Argument `IsKindOf` jest `CRuntimeClass` obiektem, który można uzyskać przy użyciu `RUNTIME_CLASS` makra z nazwą klasy.

### <a name="to-use-the-runtime_class-macro"></a>Aby użyć makra RUNTIME_CLASS

1. Użyj `RUNTIME_CLASS` z nazwą klasy, jak pokazano poniżej dla klasy `CObject` :

   [!code-cpp[NVC_MFCCObjectSample#4](codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Rzadko trzeba będzie uzyskać bezpośredni dostęp do obiektu klasy uruchomieniowej. Bardziej typowym zastosowaniem jest przekazanie obiektu klasy Run-Time do `IsKindOf` funkcji, jak pokazano w następnej procedurze. `IsKindOf`Funkcja testuje obiekt, aby sprawdzić, czy należy on do określonej klasy.

#### <a name="to-use-the-iskindof-function"></a>Aby użyć funkcji IsKindOf

1. Upewnij się, że Klasa ma obsługę klasy w czasie wykonywania. Oznacza to, że klasa musi być pochodna bezpośrednio lub pośrednio z `CObject` i była używana **Deklaracja**$ _**Dynamic** oraz `IMPLEMENT_DYNAMIC` , `DECLARE_DYNCREATE` and `IMPLEMENT_DYNCREATE` lub i i, lub, lub i i i, lub i, lub i i, lub, lub i i i, lub, lub `DECLARE_SERIAL` i i i `IMPLEMENT_SERIAL` [Deriving a Class from CObject](deriving-a-class-from-cobject.md)

1. Wywołaj `IsKindOf` funkcję członkowską dla obiektów tej klasy, używając `RUNTIME_CLASS` makra do wygenerowania `CRuntimeClass` argumentu, jak pokazano poniżej:

   [!code-cpp[NVC_MFCCObjectSample#2](codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf zwraca **wartość true** , jeśli obiekt jest elementem członkowskim określonej klasy lub klasą pochodną określonej klasy. `IsKindOf`Program nie obsługuje wielu dziedziczeń ani wirtualnych klas bazowych, ale w razie potrzeby można użyć wielokrotnego dziedziczenia dla pochodnych klas programu Microsoft Foundation.

Jednym z nich jest użycie informacji o klasie czasu wykonywania w dynamicznym tworzeniu obiektów. Ten proces jest omówiony w artykule [Tworzenie dynamicznego obiektu](dynamic-object-creation.md).

Aby uzyskać bardziej szczegółowe informacje na temat serializacji i informacji o klasie czasu wykonywania, zobacz artykuły [pliki w MFC](files-in-mfc.md) i [Serialization](serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Używanie obiektu CObject](using-cobject.md)
