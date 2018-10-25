---
title: Platform::WeakReference, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f8aa68a3a8bd94bf97f6e9a517c3f17c03ccaa5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062707"
---
# <a name="platformweakreference-class"></a>Platform::WeakReference, klasa

Reprezentuje słabe odwołanie do wystąpienia klasy ref.

## <a name="syntax"></a>Składnia

```cpp
class WeakReference
```

#### <a name="parameters"></a>Parametry

### <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Element członkowski|Opis|
|------------|-----------------|
|[Weakreference::weakreference —](#ctor)|Inicjuje nowe wystąpienie klasy WeakReference.|

### <a name="methods"></a>Metody

|Element członkowski|Opis|
|------------|-----------------|
|[Weakreference::Resolve —](#resolve)|Zwraca uchwyt do podstawowej klasy referencyjnej lub nullptr, jeśli obiekt nie jest już istnieje.|

### <a name="operators"></a>Operatory

|Element członkowski|Opis|
|------------|-----------------|
|[WeakReference::operator =](#operator-assign)|Przypisuje nową wartość do obiektu WeakReference.|
|[WeakReference::operator BoolType](#booltype)|Implementuje wzorzec bool bezpieczne.|

### <a name="remarks"></a>Uwagi

Weakreference — klasa nie jest klasą ref i dlatego nie dziedziczą z Platform::Object ^ i nie można używać w podpisie metody publicznej.

## <a name="operator-assign"></a> WeakReference::operator =

Przypisuje wartość do WeakReference.

### <a name="syntax"></a>Składnia

```cpp
WeakReference& operator=(decltype(__nullptr));
WeakReference& operator=(const WeakReference& otherArg);
WeakReference& operator=(WeakReference&& otherArg);
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg);
```

### <a name="remarks"></a>Uwagi

Ostatnie przeciążenie na powyższej liście umożliwia przypisanie klasy referencyjnej do zmiennej WeakReference. W takim przypadku klasa ref jest takiej [Platform::Object](../cppcx/platform-object-class.md)^. Później przywrócić oryginalny typ, określając ją jako argumentu dla parametru typu w [weakreference::Resolve —\<T >](#resolve) funkcja elementu członkowskiego.

## <a name="booltype"></a> WeakReference::operator BoolType

Implementuje wzorzec bezpieczne bool weakreference — klasa. Nie można jawnie wywoływana z kodu użytkownika.

### <a name="syntax"></a>Składnia

```cpp
BoolType BoolType();
```

## <a name="resolve"></a> Weakreference::Resolve — metoda (przestrzeń nazw platformy)

Zwraca uchwyt do oryginalnej klasy ref lub `nullptr` Jeśli obiekt nie jest już istnieje.

### <a name="syntax"></a>Składnia

```cpp
template<typename T>
T^ Resolve() const;
```

### <a name="parameters"></a>Parametry

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Dojście do klasy referencyjnej, która obiektu WeakReference został poprzednio powiązany z lub nullptr.

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

Należy pamiętać, że parametr typu T, T nie ^.

## <a name="ctor"></a> Weakreference::weakreference — Konstruktor

Zapewnia różne sposoby, aby skonstruować WeakReference.

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

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)