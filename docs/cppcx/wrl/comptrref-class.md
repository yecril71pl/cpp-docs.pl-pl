---
title: ComPtrRef — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
ms.openlocfilehash: df9ded817227547493c04035e0abc3d948e24495
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372633"
---
# <a name="comptrref-class"></a>ComPtrRef — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
[ComPtr\<T>](comptr-class.md) typu lub typu pochodnego z niego, a nie tylko interfejs reprezentowany przez . `ComPtr`

## <a name="remarks"></a>Uwagi

Reprezentuje odwołanie do obiektu `ComPtr<T>`typu .

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                               | Opis
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | Inicjuje nowe wystąpienie `ComPtrRef` klasy z określonego `ComPtrRef` wskaźnika do innego obiektu.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                         | Opis
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | Pobiera adres wskaźnika do interfejsu reprezentowanego przez `ComPtrRef` bieżący obiekt.
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Usuwa bieżący `ComPtrRef` obiekt i zwraca wskaźnik do wskaźnika do interfejsu, który `ComPtrRef` był reprezentowany przez obiekt.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                     | Opis
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::operator InterfaceType**](#operator-interfacetype-star-star) | Usuwa bieżący `ComPtrRef` obiekt i zwraca wskaźnik do wskaźnika do interfejsu, który `ComPtrRef` był reprezentowany przez obiekt.
[ComPtrRef::operator T*](#operator-t-star)                               | Zwraca wartość [ptr_](comptrrefbase-class.md#ptr) elementu członkowskiego danych bieżącego obiektu ComPtrRef.
[ComPtrRef::operator void**](#operator-void-star-star)                   | Usuwa bieżący `ComPtrRef` obiekt, rzutuje wskaźnik do interfejsu, który `ComPtrRef` był reprezentowany przez obiekt `void`jako wskaźnik do wskaźnika do wskaźnika do , a następnie zwraca wskaźnik rzutowania.
[ComPtrRef::operator*](#operator-star)                                   | Pobiera wskaźnik do interfejsu reprezentowane przez `ComPtrRef` bieżący obiekt.
[ComPtrRef::operator==](#operator-equality)                              | Wskazuje, czy `ComPtrRef` dwa obiekty są równe.
[ComPtrRef::operator!=](#operator-inequality)                            | Wskazuje, czy `ComPtrRef` dwa obiekty nie są równe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef::ComPtrRef

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*Ptr*<br/>
Podstawowa wartość `ComPtrRef` innego obiektu.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie `ComPtrRef` klasy z określonego `ComPtrRef` wskaźnika do innego obiektu.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef::GetAddressOf

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres wskaźnika do interfejsu reprezentowanego `ComPtrRef` przez bieżący obiekt.

### <a name="remarks"></a>Uwagi

Pobiera adres wskaźnika do interfejsu reprezentowanego przez `ComPtrRef` bieżący obiekt.

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef::operator==

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parametry

*A*<br/>
Odwołanie do `ComPtrRef` obiektu.

*B*<br/>
Odwołanie do `ComPtrRef` innego obiektu lub wskaźnik do`void*`typu anonimowego ( ).

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator daje **wartość true,** jeśli obiekt *a* jest równy obiektowi *b*; w przeciwnym razie **false**.

Drugi i trzeci operator dają **true,** jeśli *obiekt* a jest równa **nullptr**; w przeciwnym razie **false**.

Czwarty i piąty operator dają **wartość true,** jeśli obiekt *a* jest równy obiektowi *b;* w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Wskazuje, czy `ComPtrRef` dwa obiekty są równe.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef::operator!=

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parametry

*A*<br/>
Odwołanie do `ComPtrRef` obiektu.

*B*<br/>
Odwołanie do `ComPtrRef` innego obiektu lub wskaźnik do`void*`obiektu anonimowego ( ).

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator daje **wartość true,** jeśli obiekt *a* nie jest równy obiektowi *b;* w przeciwnym razie **false**.

Drugi i trzeci operator dają **true,** jeśli obiekt *a* nie jest równa **nullptr**; w przeciwnym razie **false**.

Operatory czwarte i piąte dają **wartość true,** jeśli obiekt *a* nie jest równy obiektowi *b;* w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Wskazuje, czy `ComPtrRef` dwa obiekty nie są równe.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef::operator InterfaceType**

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Uwagi

Usuwa bieżący `ComPtrRef` obiekt i zwraca wskaźnik do wskaźnika do interfejsu, który `ComPtrRef` był reprezentowany przez obiekt.

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef::operator*

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu reprezentowane `ComPtrRef` przez bieżący obiekt.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do interfejsu reprezentowane przez `ComPtrRef` bieżący obiekt.

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef::operator T*

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
operator T*();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość [ptr_](comptrrefbase-class.md#ptr) elementu członkowskiego danych bieżącego `ComPtrRef` obiektu.

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef::operator void\*\*

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Uwagi

Usuwa bieżący `ComPtrRef` obiekt, rzutuje wskaźnik do interfejsu, który `ComPtrRef` był reprezentowany przez obiekt `void`jako wskaźnik do wskaźnika do wskaźnika do , a następnie zwraca wskaźnik rzutowania.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który był `ComPtrRef` reprezentowany przez usunięty obiekt.

### <a name="remarks"></a>Uwagi

Usuwa bieżący `ComPtrRef` obiekt i zwraca wskaźnik do wskaźnika do interfejsu, który `ComPtrRef` był reprezentowany przez obiekt.
