---
title: Comptrref — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e19b8bb5ecf1215c3f9c4eb74cf36eb9d7fc7200
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235805"
---
# <a name="comptrref-class"></a>ComPtrRef — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename T
>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
A [ComPtr\<T >](../windows/comptr-class.md) typu lub typu pochodnego w nie tylko interfejs, reprezentowane przez `ComPtr`.

## <a name="remarks"></a>Uwagi

Reprezentuje odwołanie do obiektu typu `ComPtr<T>`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                               | Opis
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | Inicjuje nowe wystąpienie klasy `ComPtrRef` klasy z określonym wskaźnika `ComPtrRef` obiektu.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                         | Opis
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | Pobiera adres wskaźnika do interfejsu, reprezentowane przez bieżącą `ComPtrRef` obiektu.
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Usuwa bieżący `ComPtrRef` obiektu i zwraca wskaźnik do a wskaźnik do interfejsu, który został przedstawiony przez `ComPtrRef` obiektu.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                     | Opis
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::operator InterfaceType **](#operator-interfacetype-star-star) | Usuwa bieżący `ComPtrRef` obiektu i zwraca wskaźnik do a wskaźnik do interfejsu, który został przedstawiony przez `ComPtrRef` obiektu.
[ComPtrRef::operator T *](#operator-t-star)                               | Zwraca wartość [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) bieżącego obiektu comptrref — element członkowski danych.
[ComPtrRef::operator void **](#operator-void-star-star)                   | Spowoduje usunięcie bieżącego `ComPtrRef` obiektów, rzutuje wskaźnik do interfejsu, który został przedstawiony przez `ComPtrRef` obiektu jako wskaźnik do wskaźnik do `void`, a następnie zwraca wskaźnik rzutowania.
[ComPtrRef::operator *](#operator-star)                                   | Pobiera wskaźnik do interfejsu, reprezentowane przez bieżącą `ComPtrRef` obiektu.
[ComPtrRef::operator ==](#operator-equality)                              | Wskazuje, czy dwa `ComPtrRef` obiekty są sobie równe.
[ComPtrRef::operator! =](#operator-inequality)                            | Wskazuje, czy dwa `ComPtrRef` obiekty nie są równe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::wrl:: details

## <a name="comptrref"></a>ComPtrRef::ComPtrRef

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Podstawową wartość innego `ComPtrRef` obiektu.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `ComPtrRef` klasy z określonym wskaźnika `ComPtrRef` obiektu.

## <a name="getaddressof"></a>ComPtrRef::GetAddressOf

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres wskaźnika do interfejsu, reprezentowane przez bieżącą `ComPtrRef` obiektu.

### <a name="remarks"></a>Uwagi

Pobiera adres wskaźnika do interfejsu, reprezentowane przez bieżącą `ComPtrRef` obiektu.

## <a name="operator-equality"></a>ComPtrRef::operator ==

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*a*<br/>
Odwołanie do `ComPtrRef` obiektu.

*b*<br/>
Odwołanie do innego `ComPtrRef` obiekt lub wskaźnik do typu anonimowego (`void*`).

### <a name="return-value"></a>Wartość zwracana

Pierwszy plony operator `true` Jeśli obiekt *a* jest równy obiektowi *b*; w przeciwnym razie `false`.

Operatory drugi i trzeci uzyskanie `true` Jeśli obiekt *a* jest równa `nullptr`; w przeciwnym razie `false`.

Operatory czwarty i piąty uzyskanie `true` Jeśli obiekt *a* jest równy obiektowi *b*; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Wskazuje, czy dwa `ComPtrRef` obiekty są sobie równe.

## <a name="operator-inequality"></a>ComPtrRef::operator! =

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*a*<br/>
Odwołanie do `ComPtrRef` obiektu.

*b*<br/>
Odwołanie do innego `ComPtrRef` obiekt lub wskaźnik do obiektu anonimowego (`void*`).

### <a name="return-value"></a>Wartość zwracana

Pierwszy plony operator `true` Jeśli obiekt *a* nie jest równa obiektu *b*; w przeciwnym razie `false`.

Operatory drugi i trzeci uzyskanie `true` Jeśli obiekt *a* nie jest równa `nullptr`; w przeciwnym razie `false`.

Operatory czwarty i piąty uzyskanie `true` Jeśli obiekt *a* nie jest równa obiektu *b*; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Wskazuje, czy dwa `ComPtrRef` obiekty nie są równe.

## <a name="operator-interfacetype-star-star"></a>ComPtrRef::operator InterfaceType **

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Uwagi

Usuwa bieżący `ComPtrRef` obiektu i zwraca wskaźnik do a wskaźnik do interfejsu, który został przedstawiony przez `ComPtrRef` obiektu.

## <a name="operator-star"></a>ComPtrRef::operator *

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, reprezentowane przez bieżącą `ComPtrRef` obiektu.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do interfejsu, reprezentowane przez bieżącą `ComPtrRef` obiektu.

## <a name="operator-t-star"></a>ComPtrRef::operator T *

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
operator T*();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) element członkowski danych bieżącego `ComPtrRef` obiektu.

## <a name="operator-void-star-star"></a>ComPtrRef::operator void\*\*

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Uwagi

Spowoduje usunięcie bieżącego `ComPtrRef` obiektów, rzutuje wskaźnik do interfejsu, który został przedstawiony przez `ComPtrRef` obiektu jako wskaźnik do wskaźnik do `void`, a następnie zwraca wskaźnik rzutowania.

## <a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu, który został przedstawiony przez usunięte `ComPtrRef` obiektu.

### <a name="remarks"></a>Uwagi

Usuwa bieżący `ComPtrRef` obiektu i zwraca wskaźnik do a wskaźnik do interfejsu, który został przedstawiony przez `ComPtrRef` obiektu.
