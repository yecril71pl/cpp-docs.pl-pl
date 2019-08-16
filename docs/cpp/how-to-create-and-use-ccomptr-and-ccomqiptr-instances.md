---
title: 'Instrukcje: Tworzenie i używanie wystąpień CComPtr i CComQIPtr'
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 8dd7aa903eefd533b1dd2688f3cee46ab3787e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498595"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Instrukcje: Tworzenie i używanie wystąpień CComPtr i CComQIPtr

W klasycznym programowaniu systemu Windows biblioteki są często implementowane jako obiekty COM (lub dokładniej, jako serwery COM). Wiele składników systemu operacyjnego Windows jest implementowanych jako serwery COM, a wiele współautorów udostępnia biblioteki w tym formularzu. Aby uzyskać informacje dotyczące podstawowych informacji o modelu COM, zobacz [składnik modelu COM](/windows/win32/com/component-object-model--com--portal).

Podczas tworzenia wystąpienia obiektu Component Object Model (com) należy przechowywać wskaźnik interfejsu w inteligentnym wskaźniku com, który wykonuje zliczanie odwołań przy użyciu wywołań do `AddRef` i `Release` w destruktorze. Jeśli używasz Active Template Library (ATL) lub biblioteka MFC (MFC), użyj `CComPtr` inteligentnego wskaźnika. Jeśli nie używasz biblioteki ATL ani MFC, użyj polecenia `_com_ptr_t`. Ze względu na `std::unique_ptr`to, że model com nie jest odpowiednikiem, Użyj tych inteligentnych wskaźników zarówno dla scenariuszy z jednym właścicielem, jak i wieloma właścicielami. Obie `CComPtr` i`ComQIPtr` obsługują operacje przenoszenia, które mają odwołania rvalue.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `CComPtr` do tworzenia wystąpienia obiektu com i uzyskiwania wskaźników do interfejsów. Należy zauważyć, `CComPtr::CoCreateInstance` że funkcja członkowska jest używana do tworzenia obiektu com zamiast funkcji Win32, która ma taką samą nazwę.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr`a jego względne elementy są częścią ATL i są zdefiniowane w \<atlcomcli. h >. `_com_ptr_t`jest zadeklarowany \<w comip. h >. Kompilator tworzy specjalizacje, `_com_ptr_t` gdy generuje klasy otoki dla bibliotek typów.

## <a name="example"></a>Przykład

Ponadto program ATL `CComQIPtr`oferuje prostsze składnie służące do wykonywania zapytań względem obiektu com w celu pobrania dodatkowego interfejsu. Zaleca `CComPtr` się jednak, aby wszystko, co `CComQIPtr` można zrobić, i jest semantycznie bardziej spójne ze wskaźnikami interfejsu com RAW. W przypadku użycia `CComPtr` zapytania do interfejsu, Nowy wskaźnik interfejsu jest umieszczany w parametrze out. Jeśli wywołanie nie powiedzie się, zwracany jest wynik HRESULT, który jest typowym wzorcem modelu COM. W `CComQIPtr`przypadku, wartość zwracana jest wskaźnikiem, a jeśli wywołanie nie powiedzie się, nie można uzyskać dostępu do wewnętrznej wartości zwracanej HRESULT. W poniższych dwóch wierszach przedstawiono sposób obsługi błędów w programie `CComPtr` i `CComQIPtr` różnią się.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Przykład

`CComPtr`zapewnia specjalizację dla elementu IDispatch, który umożliwia przechowywanie wskaźników do składników automatyzacji modelu COM i wywoływanie metod w interfejsie przy użyciu późnego wiązania. `CComDispatchDriver`jest elementem TypeDef dla `CComQIPtr<IDispatch, &IIDIDispatch>`, który jest niejawnie konwertowany `CComPtr<IDispatch>`na. W związku z tym, gdy dowolne z tych trzech nazw pojawia się w kodzie, `CComPtr<IDispatch>`jest równoważne. Poniższy przykład pokazuje, jak uzyskać wskaźnik do modelu obiektów programu Microsoft Word przy użyciu `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
