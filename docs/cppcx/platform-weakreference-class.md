---
title: 'Platform:: WeakReference, Klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
ms.openlocfilehash: befefba7cc76f24f6dddd58d0c5f040bfd205508
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216599"
---
# <a name="platformweakreference-class"></a>Platform:: WeakReference, Klasa

Reprezentuje słabe odwołanie do wystąpienia klasy ref.

## <a name="syntax"></a>Składnia

```cpp
class WeakReference
```

#### <a name="parameters"></a>Parametry

### <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Członek|Opis|
|------------|-----------------|
|[WeakReference:: WeakReference](#ctor)|Inicjuje nowe wystąpienie klasy WeakReference.|

### <a name="methods"></a>Metody

|Członek|Opis|
|------------|-----------------|
|[WeakReference:: Rozwiąż](#resolve)|Zwraca dojście do bazowej klasy referencyjnej lub nullptr, jeśli obiekt już nie istnieje.|

### <a name="operators"></a>Operatory

|Członek|Opis|
|------------|-----------------|
|[WeakReference:: operator =](#operator-assign)|Przypisuje nową wartość do obiektu WeakReference.|
|[WeakReference:: operator BoolType](#booltype)|Implementuje bezpieczny wzorzec bool.|

### <a name="remarks"></a>Uwagi

Sama klasa WeakReference nie jest klasą referencyjną i dlatego nie dziedziczy z klasy platform:: Object ^ i nie może być używana w sygnaturze metody publicznej.

## <a name="weakreferenceoperator"></a><a name="operator-assign"></a>WeakReference:: operator =

Przypisuje wartość do WeakReference.

### <a name="syntax"></a>Składnia

```cpp
WeakReference& operator=(decltype(__nullptr));
WeakReference& operator=(const WeakReference& otherArg);
WeakReference& operator=(WeakReference&& otherArg);
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg);
```

### <a name="remarks"></a>Uwagi

Ostatnie Przeciążenie na powyższej liście umożliwia przypisanie klasy ref do zmiennej WeakReference. W takim przypadku Klasa ref jest downcast do [platform:: Object](../cppcx/platform-object-class.md)^. Oryginalny typ można przywrócić później przez określenie go jako argumentu parametru typu w funkcji członkowskiej [WeakReference:: Rozwiązuj \<T> ](#resolve) .

## <a name="weakreferenceoperator-booltype"></a><a name="booltype"></a>WeakReference:: operator BoolType

Implementuje bezpieczny wzorzec bool dla klasy WeakReference. Nie można jawnie wywołać w kodzie.

### <a name="syntax"></a>Składnia

```cpp
BoolType BoolType();
```

## <a name="weakreferenceresolve-method-platform-namespace"></a><a name="resolve"></a>WeakReference:: Rozwiązuj — Metoda (przestrzeń nazw platformy)

Zwraca dojście do oryginalnej klasy referencyjnej lub **`nullptr`** Jeśli obiekt już nie istnieje.

### <a name="syntax"></a>Składnia

```cpp
template<typename T>
T^ Resolve() const;
```

### <a name="parameters"></a>Parametry

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Dojście do klasy referencyjnej, z którą wcześniej skojarzono obiekt WeakReference, lub nullptr.

### <a name="example"></a>Przykład

```cpp
Bar^ bar = ref new Bar();
//use bar...

if (bar != nullptr)
{
    WeakReference wr(bar);
    Bar^ newReference = wr.Resolve<Bar>();
}
```

Należy zauważyć, że parametr type ma wartość T, a nie T ^.

## <a name="weakreferenceweakreference-constructor"></a><a name="ctor"></a>WeakReference:: WeakReference — Konstruktor

Oferuje różne sposoby konstruowania WeakReference.

### <a name="syntax"></a>Składnia

```cpp
WeakReference();
WeakReference(decltype(__nullptr));
WeakReference(const WeakReference& otherArg);
WeakReference(WeakReference&& otherArg);
explicit WeakReference(const volatile ::Platform::Object^ const otherArg);
```

### <a name="example"></a>Przykład

```cpp
MyClass^ mc = ref new MyClass();
WeakReference wr(mc);
MyClass^ copy2 = wr.Resolve<MyClass>();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
