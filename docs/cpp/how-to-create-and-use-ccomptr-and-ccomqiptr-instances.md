---
title: 'Instrukcje: Tworzenie wystąpień CComPtr i CComQIPtr oraz korzystanie z nich'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: e376eab75b9b1fb4a7a271d05fe037142f22e139
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246540"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Instrukcje: Tworzenie wystąpień CComPtr i CComQIPtr oraz korzystanie z nich

W klasycznym programowaniu systemu Windows biblioteki są często implementowane jako obiekty COM (lub dokładniej, jako serwery COM). Wiele składników systemu operacyjnego Windows jest implementowanych jako serwery COM, a wiele współautorów udostępnia biblioteki w tym formularzu. Aby uzyskać informacje na temat podstaw modelu COM, zobacz [Component Object Model (com)](/windows/win32/com/component-object-model--com--portal).

Podczas tworzenia wystąpienia obiektu Component Object Model (COM) należy przechowywać wskaźnik interfejsu w inteligentnym wskaźniku COM, który wykonuje zliczanie odwołań przy użyciu wywołań do `AddRef` i `Release` w destruktorze. Jeśli używasz Active Template Library (ATL) lub biblioteka MFC (MFC), Użyj inteligentnego wskaźnika `CComPtr`. Jeśli nie używasz biblioteki ATL ani MFC, użyj `_com_ptr_t`. Ze względu na to, że nie ma modelu COM równoważnego `std::unique_ptr`, Użyj tych inteligentnych wskaźników zarówno dla scenariuszy z jednym właścicielem, jak i wieloma właścicielami. Zarówno `CComPtr`, jak i `ComQIPtr` obsługują operacje przenoszenia, które mają odwołania rvalue.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `CComPtr` do tworzenia wystąpienia obiektu COM i uzyskiwania wskaźników do interfejsów. Należy zauważyć, że funkcja członkowska `CComPtr::CoCreateInstance` jest używana do tworzenia obiektu COM zamiast funkcji Win32, która ma taką samą nazwę.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` i jego względne elementy są częścią ATL i są zdefiniowane w \<atlcomcli. h >. `_com_ptr_t` jest zadeklarowana w \<comip. h >. Kompilator tworzy specjalizacje `_com_ptr_t`, gdy generuje klasy otoki dla bibliotek typów.

## <a name="example"></a>Przykład

ATL udostępnia również `CComQIPtr`, która ma prostsze składnię do wykonywania zapytań względem obiektu COM w celu pobrania dodatkowego interfejsu. Zaleca się jednak `CComPtr`, ponieważ robi to wszystko, co `CComQIPtr` może zrobić i jest semantycznie bardziej spójny ze wskaźnikami interfejsu COM raw. Jeśli użyjesz `CComPtr` do zapytania o interfejs, Nowy wskaźnik interfejsu zostanie umieszczony w parametrze out. Jeśli wywołanie nie powiedzie się, zwracany jest wynik HRESULT, który jest typowym wzorcem modelu COM. Przy `CComQIPtr`wartość zwracana jest wskaźnikiem, a jeśli wywołanie nie powiedzie się, nie można uzyskać dostępu do wewnętrznej wartości zwracanej HRESULT. W poniższych dwóch wierszach pokazano, jak są różne mechanizmy obsługi błędów w `CComPtr` i `CComQIPtr`.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Przykład

`CComPtr` zapewnia specjalizację dla elementu IDispatch, który umożliwia przechowywanie wskaźników do składników automatyzacji modelu COM i wywoływanie metod w interfejsie przy użyciu późnego wiązania. `CComDispatchDriver` jest elementem TypeDef dla `CComQIPtr<IDispatch, &IIDIDispatch>`, który jest niejawnie konwertowany na `CComPtr<IDispatch>`. W związku z tym, gdy dowolna z tych trzech nazw pojawia się w kodzie, jest równoważne `CComPtr<IDispatch>`. Poniższy przykład pokazuje, jak uzyskać wskaźnik do modelu obiektów programu Microsoft Word przy użyciu `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
