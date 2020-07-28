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
ms.openlocfilehash: f92a3e14018cf8c02dec40b664b72a0956f6220e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220538"
---
# <a name="comptrref-class"></a>ComPtrRef — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ [ComPtr \<T> ](comptr-class.md) lub typ pochodzący od niego, nie tylko interfejs reprezentowany przez `ComPtr` .

## <a name="remarks"></a>Uwagi

Reprezentuje odwołanie do obiektu typu `ComPtr<T>` .

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                               | Opis
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef:: ComPtrRef](#comptrref) | Inicjuje nowe wystąpienie `ComPtrRef` klasy od określonego wskaźnika do innego `ComPtrRef` obiektu.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                         | Opis
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef:: GetAddressOf](#getaddressof)                     | Pobiera adres wskaźnika do interfejsu reprezentowanego przez bieżący `ComPtrRef` obiekt.
[ComPtrRef:: ReleaseAndGetAddressOf —](#releaseandgetaddressof) | Usuwa bieżący `ComPtrRef` obiekt i zwraca wskaźnik do interfejsu, który został reprezentowany przez `ComPtrRef` obiekt.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                     | Opis
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef:: operator InterfaceType * *](#operator-interfacetype-star-star) | Usuwa bieżący `ComPtrRef` obiekt i zwraca wskaźnik do interfejsu, który został reprezentowany przez `ComPtrRef` obiekt.
[ComPtrRef:: operator T *](#operator-t-star)                               | Zwraca wartość elementu członkowskiego danych [ptr_](comptrrefbase-class.md#ptr) bieżącego obiektu ComPtrRef.
[ComPtrRef:: operator void * *](#operator-void-star-star)                   | Usuwa bieżący `ComPtrRef` obiekt, rzutuje wskaźnik do interfejsu, który został reprezentowany przez `ComPtrRef` obiekt jako wskaźnik do wskaźnika do **`void`** , a następnie zwraca wskaźnik rzutowania.
[ComPtrRef:: operator *](#operator-star)                                   | Pobiera wskaźnik do interfejsu reprezentowanego przez bieżący `ComPtrRef` obiekt.
[ComPtrRef:: operator = =](#operator-equality)                              | Wskazuje, czy dwa `ComPtrRef` obiekty są równe.
[ComPtrRef:: operator! =](#operator-inequality)                            | Wskazuje, czy dwa `ComPtrRef` obiekty nie są równe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Client. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef:: ComPtrRef

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wartość bazowa innego `ComPtrRef` obiektu.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie `ComPtrRef` klasy od określonego wskaźnika do innego `ComPtrRef` obiektu.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef:: GetAddressOf

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres wskaźnika do interfejsu reprezentowanego przez bieżący `ComPtrRef` obiekt.

### <a name="remarks"></a>Uwagi

Pobiera adres wskaźnika do interfejsu reprezentowanego przez bieżący `ComPtrRef` obiekt.

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef:: operator = =

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*z*<br/>
Odwołanie do `ComPtrRef` obiektu.

*b*<br/>
Odwołanie do innego `ComPtrRef` obiektu lub wskaźnik do typu anonimowego ( **`void*`** ).

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator daje **`true`** , że obiekt *a* jest równy obiektowi *b*; w przeciwnym razie **`false`** .

Drugi i trzeci operator **`true`** uzyskują wartość, jeśli obiekt *a* jest równy **`nullptr`** ; w przeciwnym razie **`false`** .

Czwarte i piąte operatory dają **`true`** , czy obiekt *a* jest równy obiektowi *b*; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Wskazuje, czy dwa `ComPtrRef` obiekty są równe.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef:: operator! =

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*z*<br/>
Odwołanie do `ComPtrRef` obiektu.

*b*<br/>
Odwołanie do innego `ComPtrRef` obiektu lub wskaźnik do anonimowego obiektu ( **`void*`** ).

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator daje **`true`** , że obiekt *a* nie jest równy obiektowi *b*; w przeciwnym razie **`false`** .

Drugi i trzeci operator **`true`** uzyskują wartość, jeśli obiekt *a* nie jest równy **`nullptr`** ; w przeciwnym razie **`false`** .

Czwarte i piąte operatory dają **`true`** , czy obiekt *a* nie jest równy obiektowi *b*; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Wskazuje, czy dwa `ComPtrRef` obiekty nie są równe.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef:: operator InterfaceType\*\*

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Uwagi

Usuwa bieżący `ComPtrRef` obiekt i zwraca wskaźnik do interfejsu, który został reprezentowany przez `ComPtrRef` obiekt.

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef:: operator *

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu reprezentowanego przez bieżący `ComPtrRef` obiekt.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do interfejsu reprezentowanego przez bieżący `ComPtrRef` obiekt.

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef:: operator T *

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
operator T*();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość elementu członkowskiego danych [ptr_](comptrrefbase-class.md#ptr) bieżącego `ComPtrRef` obiektu.

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef:: operator void\*\*

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Uwagi

Usuwa bieżący `ComPtrRef` obiekt, rzutuje wskaźnik do interfejsu, który został reprezentowany przez `ComPtrRef` obiekt jako wskaźnik do wskaźnika do **`void`** , a następnie zwraca wskaźnik rzutowania.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtrRef:: ReleaseAndGetAddressOf —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który został reprezentowany przez usunięty `ComPtrRef` obiekt.

### <a name="remarks"></a>Uwagi

Usuwa bieżący `ComPtrRef` obiekt i zwraca wskaźnik do interfejsu, który został reprezentowany przez `ComPtrRef` obiekt.
