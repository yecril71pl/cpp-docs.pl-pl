---
title: "Porady: tworzenie i używanie CComPtr i CComQIPtr wystąpień | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 342fd293983840257e83e287df3a8ef6767826c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Porady: tworzenie wystąpień CComPtr i CComQIPtr i korzystanie z nich
W klasycznym programowania w języku systemu Windows, bibliotek często są zaimplementowane jako obiekty COM (i bardziej precyzyjnie serwerów COM). Wiele składników systemu operacyjnego Windows są zaimplementowane jako serwerów COM i wiele współautorzy zapewnia biblioteki w tym formularzu. Aby uzyskać informacje dotyczące podstawowych informacji o modelu COM, zobacz [składnik modelu COM.](http://msdn.microsoft.com/en-us/3578ca42-a4b6-44b3-ad5b-aeb5fa61f3f4).  
  
 Gdy wystąpienia obiektu modelu COM (Component Object), są przechowywane wskaźnika interfejsu w wskaźnika inteligentnego COM, który przeprowadza zliczanie za pomocą wywołania `AddRef` i `Release` w destruktor. Jeśli używasz Active Template Library (ATL) lub biblioteka Microsoft Foundation Class (MFC), użyj `CComPtr` wskaźnika inteligentnego. Jeśli nie używasz ATL ani MFC, użyj `_com_ptr_t`. Ponieważ nie istnieje żadne COM odpowiednikiem `std::unique_ptr`, użyj te wskaźniki inteligentne w scenariuszach zarówno właściciel jednym i wielu właściciela. Zarówno `CComPtr` i `ComQIPtr` operacje, zawierające odwołania do r-wartości są przenoszone z pomocy technicznej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `CComPtr` do tworzenia wystąpienia obiektu COM i uzyskać wskaźniki do jego interfejsy. Zwróć uwagę, że `CComPtr::CoCreateInstance` funkcja członkowska jest używany do tworzenia obiektu COM, zamiast funkcji Win32, który ma taką samą nazwę.  
  
 [!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]  
  
 `CComPtr`i jego odmian są częścią ATL są zdefiniowane w atlcomcli.h. `_com_ptr_t`jest zadeklarowana w comip.h. Kompilator tworzy specjalizacjach `_com_ptr_t` podczas generowania klasy otoki dla biblioteki typów.  
  
## <a name="example"></a>Przykład  
 Udostępnia również ATL `CComQIPtr`, mającego prostsze składni zapytań obiektu COM można pobrać dodatkowe interfejs. Firma Microsoft zaleca jednak `CComPtr` gdyż wszystko, co który `CComQIPtr` możliwość i jest semantycznie bardziej spójny z wskaźników interfejsów COM. raw. Jeśli używasz `CComPtr` dla interfejsu kwerendy, nowe wskaźnika interfejsu jest umieszczany w parametrem out. Jeśli połączenie nie powiedzie się, jest zwracany HRESULT, która jest typowy wzorzec COM. Z `CComQIPtr`, zwracana wartość jest wskaźnik sam i jeśli połączenie nie powiedzie się, zwracana wartość HRESULT wewnętrzny jest niedostępny. Następujące dwa wiersze nie są wyświetlane jak błąd mechanizmów obsługi `CComPtr` i `CComQIPtr` różnią się.  
  
 [!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]  
  
## <a name="example"></a>Przykład  
 `CComPtr`zapewnia specjalizacji IDispatch, umożliwiającą Zapisz wskaźniki do automatyzacji COM — składniki i wywoływać metod interfejsu za pomocą późnego wiązania. `CComDispatchDriver`jest elementem typedef dla `CComQIPtr<IDispatch, &IIDIDispatch>`, który jest niejawnie przekonwertować `CComPtr<IDispatch>`. W związku z tym, gdy zostanie wyświetlone dowolne z tych trzech nazw w kodzie, jest odpowiednikiem `CComPtr<IDispatch>`. Poniższy przykład przedstawia sposób uzyskać wskaźnik do modelu obiektów programu Microsoft Word za pomocą `CComPtr<IDispatch>`.  
  
 [!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md)