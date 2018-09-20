---
title: Comptrref — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4ec1139efae422035ef34030cfcffcc5547f0a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418505"
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

#### <a name="parameters"></a>Parametry

*T*<br/>
A [ComPtr\<T >](../windows/comptr-class.md) typu lub typu pochodnego w nie tylko interfejs, reprezentowane przez `ComPtr`.

## <a name="remarks"></a>Uwagi

Reprezentuje odwołanie do obiektu typu `ComPtr<T>`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ComPtrRef::ComPtrRef, konstruktor](../windows/comptrref-comptrref-constructor.md)|Inicjuje nowe wystąpienie klasy **comptrref —** klasy z określonym wskaźnika **comptrref —** obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ComPtrRef::GetAddressOf, metoda](../windows/comptrref-getaddressof-method.md)|Pobiera adres wskaźnika do interfejsu, reprezentowane przez bieżącą **comptrref —** obiektu.|
|[ComPtrRef::ReleaseAndGetAddressOf, metoda](../windows/comptrref-releaseandgetaddressof-method.md)|Usuwa bieżący **comptrref —** obiektu i zwraca wskaźnik do a wskaźnik do interfejsu, który został przedstawiony przez **comptrref —** obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator ComPtrRef::operator InterfaceType**](../windows/comptrref-operator-interfacetype-star-star-operator.md)|Usuwa bieżący **comptrref —** obiektu i zwraca wskaźnik do a wskaźnik do interfejsu, który został przedstawiony przez **comptrref —** obiektu.|
|[Operator ComPtrRef::operator T*](../windows/comptrref-operator-t-star-operator.md)|Zwraca wartość [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) bieżącego obiektu comptrref — element członkowski danych.|
|[Operator ComPtrRef::operator void**](../windows/comptrref-operator-void-star-star-operator.md)|Usuwa bieżący **comptrref —** obiektów, wskaźnik do interfejsu, który został przedstawiony przez rzutuje **comptrref —** obiektu jako wskaźnik do wskaźnik do **void**, a następnie Zwraca wskaźnik rzutowania.|
|[Operator ComPtrRef::operator*](../windows/comptrref-operator-star-operator.md)|Pobiera wskaźnik do interfejsu, reprezentowane przez bieżącą **comptrref —** obiektu.|
|[Operator ComPtrRef::operator==](../windows/comptrref-operator-equality-operator.md)|Wskazuje, czy dwa **comptrref —** obiekty są sobie równe.|
|[Operator ComPtrRef::operator!=](../windows/comptrref-operator-inequality-operator.md)|Wskazuje, czy dwa **comptrref —** obiekty nie są równe.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)