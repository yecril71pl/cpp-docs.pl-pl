---
title: Comptr — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88d3af154993bea6df509a69b832223aede7ad81
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386512"
---
# <a name="comptr-class"></a>ComPtr — Klasa

Tworzy *inteligentny wskaźnik* typ, który reprezentuje interfejs określony przez parametr szablonu. **ComPtr** automatycznie przechowuje licznik odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs gdy liczba odwołań osiąga zero.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs, **ComPtr** reprezentuje.

*U*<br/>
Klasa, do którego bieżący **ComPtr** jest zaprzyjaźniony. (Szablonu, który jest używany ten parametr jest chroniony).

## <a name="remarks"></a>Uwagi

`ComPtr<>` deklaruje typ, który reprezentuje podstawowego wskaźnika interfejsu. Użyj `ComPtr<>` zadeklarować zmienną, a następnie użyć operatora dostępu do elementu członkowskiego strzałkę (`->`) na dostęp do funkcji składowej interfejsu.

Aby uzyskać więcej informacji dotyczących inteligentnych wskaźników, zobacz podsekcję "Inteligentne wskaźniki COM" [praktyk kodowania COM](/windows/desktop/LearnWin32/com-coding-practices)w bibliotece MSDN.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`InterfaceType`|Synonim dla typu określonego przez *T* parametru szablonu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ComPtr::ComPtr, konstruktor](../windows/comptr-comptr-constructor.md)|Aktywuje nowe wystąpienie klasy **ComPtr** klasy. Przeciążenia zawierają konstruktory domyślne, kopiowanie, przenoszenie i konwersji.|
|[ComPtr::~ComPtr, destruktor](../windows/comptr-tilde-comptr-destructor.md)|Wyłącza wystąpienie **ComPtr**.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ComPtr::As, metoda](../windows/comptr-as-method.md)|Zwraca **ComPtr** obiekt, który reprezentuje interfejs identyfikowane za pomocą parametru określonego szablonu.|
|[ComPtr::AsIID, metoda](../windows/comptr-asiid-method.md)|Zwraca **ComPtr** obiekt, który reprezentuje interfejs identyfikowane przez identyfikator określonego interfejsu.|
|[ComPtr::AsWeak, metoda](../windows/comptr-asweak-method.md)|Pobiera słabe odwołanie do bieżącego obiektu.|
|[ComPtr::Attach, metoda](../windows/comptr-attach-method.md)|To skojarzenie **ComPtr** z typu interfejsu, określonego przez bieżący parametrowi typu szablonu.|
|[ComPtr::CopyTo, metoda](../windows/comptr-copyto-method.md)|Kopiuje skojarzony z tym interfejs bieżącej lub określonej **ComPtr** wskaźnik określonym produktem wyjściowym.|
|[ComPtr::Detach, metoda](../windows/comptr-detach-method.md)|Powoduje to usunięcie **ComPtr** z interfejsu, który reprezentuje.|
|[ComPtr::Get, metoda](../windows/comptr-get-method.md)|Pobiera wskaźnik do interfejsu, który jest skojarzony z tym **ComPtr**.|
|[ComPtr::GetAddressOf, metoda](../windows/comptr-getaddressof-method.md)|Pobiera adres [ptr_ — element](../windows/comptr-ptr-data-member.md) element członkowski danych, który zawiera wskaźnik do interfejsu, reprezentowane przez to **ComPtr**.|
|[ComPtr::ReleaseAndGetAddressOf, metoda](../windows/comptr-releaseandgetaddressof-method.md)|Zwalnia interfejs skojarzony z tym **ComPtr** i następnie pobiera adres [ptr_ — element](../windows/comptr-ptr-data-member.md) element członkowski danych, który zawiera wskaźnik do interfejsu, który został wydany.|
|[ComPtr::Reset](../windows/comptr-reset.md)|Zwalnia wszystkie odwołania dla wskaźnika do interfejsu, który jest skojarzony z tym **ComPtr**.|
|[ComPtr::Swap, metoda](../windows/comptr-swap-method.md)|Wymienia interfejsu zarządzany przez bieżący **ComPtr** przy użyciu interfejsu, zarządzana przez określony **ComPtr**.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[ComPtr::InternalAddRef, metoda](../windows/comptr-internaladdref-method.md)|Zwiększa liczbę odwołań interfejsu skojarzony z tym **ComPtr**.|
|[ComPtr::InternalRelease, metoda](../windows/comptr-internalrelease-method.md)|Wykonuje operację wydania COM w interfejsie skojarzony z tym **ComPtr**.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator ComPtr::operator Microsoft::WRL::Details::BoolType](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|Wskazuje, czy **ComPtr** Zarządzanie okresem istnienia interfejsu.|
|[Operator ComPtr::operator&](../windows/comptr-operator-ampersand-operator.md)|Pobiera adres bieżącej **ComPtr**.|
|[Operator ComPtr::operator=](../windows/comptr-operator-assign-operator.md)|Przypisuje wartość do bieżącego **ComPtr**.|
|[Operator ComPtr::operator->](../windows/comptr-operator-arrow-operator.md)|Pobiera wskaźnik do typu określonego przez parametr bieżącego szablonu.|
|[Operator ComPtr::operator==](../windows/comptr-operator-equality-operator.md)|Wskazuje, czy dwa **ComPtr** obiekty są sobie równe.|
|[Operator ComPtr::operator!=](../windows/comptr-operator-inequality-operator.md)|Wskazuje, czy dwa **ComPtr** obiekty nie są równe.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[ComPtr::ptr_, składowa danych](../windows/comptr-ptr-data-member.md)|Zawiera wskaźnik do interfejsu, który jest skojarzony z i zarządzanego przez to **ComPtr**.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)