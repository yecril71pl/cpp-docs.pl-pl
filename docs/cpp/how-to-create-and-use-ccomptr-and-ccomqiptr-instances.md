---
title: 'Instrukcje: Tworzenie wystąpień CComPtr i CComQIPtr i korzystanie z nich'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 4d3a9f98f4f4111e88a41f9d4a96cb3caefe64d8
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414636"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Instrukcje: Tworzenie wystąpień CComPtr i CComQIPtr i korzystanie z nich

W klasycznym programowaniu systemu Windows biblioteki są często implementowane jako obiekty COM (lub dokładniej, jako serwery COM). Wiele składników systemu operacyjnego Windows jest implementowanych jako serwery COM, a wiele współautorów udostępnia biblioteki w tym formularzu. Aby uzyskać informacje na temat podstaw modelu COM, zobacz [Component Object Model (com)](/windows/win32/com/component-object-model--com--portal).

Podczas tworzenia wystąpienia obiektu Component Object Model (COM) należy przechowywać wskaźnik interfejsu w inteligentnym wskaźniku COM, który wykonuje zliczanie odwołań przy użyciu wywołań do `AddRef` i `Release` w destruktorze. Jeśli używasz Active Template Library (ATL) lub biblioteka MFC (MFC), użyj `CComPtr` inteligentnego wskaźnika. Jeśli nie używasz biblioteki ATL ani MFC, użyj polecenia `_com_ptr_t` . Ze względu na to, że model COM nie jest odpowiednikiem `std::unique_ptr` , Użyj tych inteligentnych wskaźników zarówno dla scenariuszy z jednym właścicielem, jak i wieloma właścicielami. Obie `CComPtr` i `ComQIPtr` obsługują operacje przenoszenia, które mają odwołania rvalue.

## <a name="example-ccomptr"></a>Przykład: CComPtr

Poniższy przykład pokazuje, jak używać `CComPtr` do tworzenia wystąpienia obiektu com i uzyskiwania wskaźników do interfejsów. Należy zauważyć, że `CComPtr::CoCreateInstance` funkcja członkowska jest używana do tworzenia obiektu com zamiast funkcji Win32, która ma taką samą nazwę.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` a jego względne elementy są częścią ATL i są zdefiniowane w \<atlcomcli.h> . `_com_ptr_t` jest zadeklarowany w \<comip.h> . Kompilator tworzy specjalizacje, `_com_ptr_t` gdy generuje klasy otoki dla bibliotek typów.

## <a name="example-ccomqipt"></a>Przykład: CComQIPt

Ponadto program ATL oferuje `CComQIPtr` prostsze składnie służące do wykonywania zapytań względem obiektu com w celu pobrania dodatkowego interfejsu. Zaleca się jednak, `CComPtr` aby wszystko, co `CComQIPtr` można zrobić, i jest semantycznie bardziej spójne ze wskaźnikami interfejsu com RAW. W przypadku użycia `CComPtr` zapytania do interfejsu, Nowy wskaźnik interfejsu jest umieszczany w parametrze out. Jeśli wywołanie nie powiedzie się, zwracany jest wynik HRESULT, który jest typowym wzorcem modelu COM. W przypadku `CComQIPtr` , wartość zwracana jest wskaźnikiem, a jeśli wywołanie nie powiedzie się, nie można uzyskać dostępu do wewnętrznej wartości zwracanej HRESULT. W poniższych dwóch wierszach przedstawiono sposób obsługi błędów w programie `CComPtr` i `CComQIPtr` różnią się.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example-idispatch"></a>Przykład: IDispatch

`CComPtr` zapewnia specjalizację dla elementu IDispatch, który umożliwia przechowywanie wskaźników do składników automatyzacji modelu COM i wywoływanie metod w interfejsie przy użyciu późnego wiązania. `CComDispatchDriver` jest elementem TypeDef dla `CComQIPtr<IDispatch, &IIDIDispatch>` , który jest niejawnie konwertowany na `CComPtr<IDispatch>` . W związku z tym, gdy dowolne z tych trzech nazw pojawia się w kodzie, jest równoważne `CComPtr<IDispatch>` . Poniższy przykład pokazuje, jak uzyskać wskaźnik do modelu obiektów programu Microsoft Word przy użyciu `CComPtr<IDispatch>` .

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Inteligentne wskaźniki (nowoczesne C++)](../cpp/smart-pointers-modern-cpp.md)
