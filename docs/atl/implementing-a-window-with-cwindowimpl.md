---
title: Implementowanie okna przy użyciu klasy CWindowImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CWindowImpl
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb783c35704f87a0bfed57e05f22c3b9b035498
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851548"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementowanie okna przy użyciu klasy CWindowImpl
Aby zaimplementować okno, należy wyprowadzić klasę z `CWindowImpl`. W klasie pochodnej Zadeklaruj mapy komunikatów i funkcji obsługi komunikatów. Można teraz użyć klasy na trzy różne sposoby:  
  
-   [Tworzenie okna, w oparciu o nową klasę Windows](#_atl_creating_a_window_based_on_a_new_windows_class)  
  
-   [Superklasie istniejącej klasy Windows](#_atl_superclassing_an_existing_windows_class)  
  
-   [Podklasy istniejącego okna](#_atl_subclassing_an_existing_window)  
  
##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Tworzenie okna, w oparciu o nową klasę Windows  
 `CWindowImpl` zawiera [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) makra, aby zadeklarować informacji o klasie Windows. To makro implementuje `GetWndClassInfo` funkcji, która używa [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) zdefiniować informacje dotyczące nowej klasy Windows. Gdy `CWindowImpl::Create` nazywa to Windows klasa jest rejestrowana i tworzone jest nowe okno.  
  
> [!NOTE]
>  `CWindowImpl` przekazuje wartość NULL, aby `DECLARE_WND_CLASS` makra, która oznacza, że ATL wygeneruje nazwę klasy Windows. Aby określić własną nazwę, należy przekazać ciągu do DECLARE_WND_CLASS w swojej `CWindowImpl`-klasy pochodnej.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się przykład klasy, która implementuje okna, w oparciu o nową klasę Windows:  
  
 [!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]  
  
 Można utworzyć okna, Utwórz wystąpienie obiektu `CMyWindow` , a następnie wywołać `Create` metody.  
  
> [!NOTE]
>  Aby zastąpić domyślne Windows klasy informacje, należy zaimplementować `GetWndClassInfo` metody w klasie pochodnej, ustawiając `CWndClassInfo` członków odpowiednie wartości.  
  
##  <a name="_atl_superclassing_an_existing_windows_class"></a> Superclassing istniejącej klasy Windows  
 [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) — makro służy do tworzenia okna tego superklas Windows istniejącej klasy. Określ to makro użytkownika `CWindowImpl`-klasy pochodnej. Podobnie jak inne okno ATL komunikaty są obsługiwane przez mapy komunikatów.  
  
 Korzystając z DECLARE_WND_SUPERCLASS nową klasę Windows zostanie zarejestrowana. Ta nowa klasa będzie taka sama jak istniejąca klasa określić, ale będzie zastąpić procedurę okna z `CWindowImpl::WindowProc` (lub funkcją, która zastępuje tę metodę).  
  
## <a name="example"></a>Przykład  
 Następujące jest przykładem klasy tego superklas edycji standard klasy:  
  
 [!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]  
  
 Aby utworzyć podklasy okno edycji, Utwórz wystąpienie obiektu `CMyEdit` , a następnie wywołać `Create` metody.  
  
##  <a name="_atl_subclassing_an_existing_window"></a> Tworzenie podklasy istniejącego okna  
 Do podklasy istniejącego okna, należy wyprowadzić klasę z `CWindowImpl` i Zadeklaruj mapy komunikatów, tak jak w poprzednich dwóch przypadków. Należy jednak pamiętać, że nie określisz żadnych informacji o klasie Windows, ponieważ będzie podklasy istniejącego już okna.  
  
 Zamiast wywoływać metodę `Create`, wywołaj `SubclassWindow` i przekaż go dojście do istniejącego okna, aby podklasy. Gdy okno jest podklasą klasy, zostanie użyty `CWindowImpl::WindowProc` (lub funkcję, która zastępuje tę metodę) do przekierowywania komunikatów do mapy komunikatów. Aby odłączyć będące podklasami okna z obiektu, wywołaj `UnsubclassWindow`. Następnie w oknie oryginalnego procedurę okna zostaną przywrócone.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)

