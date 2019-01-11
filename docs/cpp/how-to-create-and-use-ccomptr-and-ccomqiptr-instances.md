---
title: 'Instrukcje: Tworzenie i używanie CComPtr i CComQIPtr wystąpień'
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 2bcabfe80185939b899c84fc44f71b98608fc3c7
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220554"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Instrukcje: Tworzenie i używanie CComPtr i CComQIPtr wystąpień

W klasycznym programowaniu Windows, bibliotek są często implementowane jako obiekty COM (lub dokładniej, jako serwery COM). Wiele składników systemu operacyjnego Windows są implementowane jako serwerów COM, a wiele współautorzy podają bibliotek w tym formularzu. Aby uzyskać informacje dotyczące podstawowych informacji o modelu COM, zobacz [składnik modelu COM](/windows/desktop/com/component-object-model--com--portal).

Podczas tworzenia wystąpienia obiektu Component Object Model (COM) przechowywania wskaźnik interfejsu w modelu COM inteligentny wskaźnik, który wykonuje liczenia odwołań przy użyciu wywołania `AddRef` i `Release` w destruktorze. Jeśli używasz Active Template Library (ATL) lub biblioteki Microsoft Foundation Class (MFC), należy użyć `CComPtr` inteligentnego wskaźnika. Jeśli nie używasz biblioteki ATL lub MFC, należy użyć `_com_ptr_t`. Ponieważ COM nie jest odpowiednikiem `std::unique_ptr`, używaj tych inteligentnych wskaźników dla scenariuszy z jednego właściciela i wielu właściciela. Zarówno `CComPtr` i `ComQIPtr` obsługę przenoszenia operacji, które mają odwołania rvalue.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `CComPtr` do tworzenia wystąpienia obiektu COM i uzyskać wskaźniki do jego interfejsów. Należy zauważyć, że `CComPtr::CoCreateInstance` funkcja członkowska jest używany do tworzenia obiektu COM, zamiast funkcji Win32, który ma taką samą nazwę.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` i jego odmian są częścią ATL i są definiowane w \<atlcomcli.h >. `_com_ptr_t` jest zadeklarowana w \<comip.h >. Kompilator tworzy specjalizacje `_com_ptr_t` podczas generowania klasy otoki dla biblioteki typów.

## <a name="example"></a>Przykład

ATL udostępnia również `CComQIPtr`, mającym prostsze składni zapytań obiekt COM, można pobrać dodatkowe interfejsu. Firma Microsoft zaleca jednak `CComPtr` ponieważ robi wszystko, co który `CComQIPtr` zrobić i semantycznie bardziej spójny z surowe wskaźniki interfejsu COM. Jeśli używasz `CComPtr` kwerendy dla interfejsu, nowy wskaźnik interfejsu, jest umieszczany w parametrze wyjściowym. Jeśli wywołanie zakończy się niepowodzeniem, zwracana jest wartość HRESULT, który jest typowy wzorzec COM. Za pomocą `CComQIPtr`, zwracana jest wartość wskaźnika, sama i jeśli wywołanie zakończy się niepowodzeniem, wewnętrzne zwracanej wartości HRESULT nie są dostępne. Następujące dwa wiersze nie są wyświetlane jak błąd mechanizmów obsługi `CComPtr` i `CComQIPtr` różnią się.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Przykład

`CComPtr` zapewnia specjalizacji IDispatch, która umożliwia przechowywanie wskaźniki do składników automatyzacji COM i wywołania metody w interfejsie przy użyciu późne powiązania. `CComDispatchDriver` element typedef dla jest `CComQIPtr<IDispatch, &IIDIDispatch>`, który jest niejawnie konwertowany na `CComPtr<IDispatch>`. W związku z tym, gdy dowolne z tych trzech nazw pojawi się w kodzie, jest to równoważne `CComPtr<IDispatch>`. Poniższy przykład pokazuje, jak uzyskać wskaźnik do modelu obiektów programu Microsoft Word przy użyciu `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
