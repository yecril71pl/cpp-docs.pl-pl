---
title: Implementowanie okno z CWindowImpl | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b9c1fc32d2265f6853c4dd34a3eb463609fca52b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementowanie okno z CWindowImpl
Aby zaimplementować okno, klasa wyprowadzona z `CWindowImpl`. W klasie pochodnej zadeklarować mapy komunikatów i funkcji programu obsługi wiadomości. Można teraz używać własnej klasy na trzy różne sposoby:  
  
-   [Tworzenie okna, w oparciu o nowe klasy systemu Windows](#_atl_creating_a_window_based_on_a_new_windows_class)  
  
-   [Superklasie istniejącej klasy systemu Windows](#_atl_superclassing_an_existing_windows_class)  
  
-   [Podklasy istniejącego okna](#_atl_subclassing_an_existing_window)  
  
##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Tworzenie okna, w oparciu o nowe klasy systemu Windows  
 `CWindowImpl` zawiera [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) makra, aby zadeklarować informacji o klasie systemu Windows. Implementuje to makro `GetWndClassInfo` funkcji, która używa [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) można zdefiniować informacje dotyczące nowej klasy systemu Windows. Gdy `CWindowImpl::Create` nosi to Windows zarejestrować klasy i zostanie utworzone nowe okno.  
  
> [!NOTE]
>  `CWindowImpl` przekazuje **NULL** do `DECLARE_WND_CLASS` makra, co oznacza ATL wygeneruje nazwę klasy systemu Windows. Aby określić własną nazwę, należy przekazać ciąg `DECLARE_WND_CLASS` w Twojej `CWindowImpl`-klasy.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykładowy klasy, która implementuje okna, w oparciu o nowe klasy systemu Windows:  
  
 [!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]  
  
 Można utworzyć okna, Utwórz wystąpienie `CMyWindow` , a następnie wywołać **Utwórz** metody.  
  
> [!NOTE]
>  Aby zastąpić domyślne informacje klasy systemu Windows, należy zaimplementować `GetWndClassInfo` metody w klasie pochodnej, ustawiając `CWndClassInfo` członków odpowiednie wartości.  
  
##  <a name="_atl_superclassing_an_existing_windows_class"></a> Tworzenie nadklas istniejącej klasy systemu Windows  
 [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) makro służy do tworzenia okna tego nadklas istniejącymi systemu Windows klasy. Określ to makro użytkownika `CWindowImpl`-klasy. Podobnie jak inne okno ATL komunikaty są obsługiwane przez mapy komunikatów.  
  
 Jeśli używasz `DECLARE_WND_SUPERCLASS`, nową klasę systemu Windows zostanie zarejestrowany. Ta nowa klasa będzie taka sama jak istniejącej klasy określić, ale będzie zastąpić procedurę okna z `CWindowImpl::WindowProc` (lub funkcją, która zastępuje tę metodę).  
  
## <a name="example"></a>Przykład  
 Po jest przykładem klasy tej edycji standard nadklas klasy:  
  
 [!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]  
  
 Aby utworzyć podklasy okno edycji, Utwórz wystąpienie `CMyEdit` , a następnie wywołać **Utwórz** metody.  
  
##  <a name="_atl_subclassing_an_existing_window"></a> Tworzenie podklas istniejącego okna  
 Do podklasy istniejącego okna wyprowadzenia klasy z `CWindowImpl` ani deklarować mapy komunikatów, jak w poprzednich dwóch przypadków. Należy jednak pamiętać, że nie określaj żadnych informacji o klasie systemu Windows, ponieważ będzie podklasy już istniejącego okna.  
  
 Zamiast wywoływać metodę **Utwórz**, wywołaj `SubclassWindow` i przekaż go dojście do istniejącego okna chcesz podklasy. Gdy okno jest podklasą klasy, zostanie użyty `CWindowImpl::WindowProc` (lub funkcji zastępujący tej metody) do kierowania wiadomości do mapy wiadomości. Aby odłączyć podklasą okno z obiektu, należy wywołać `UnsubclassWindow`. Następnie w oknie oryginalną procedurę okna zostaną przywrócone.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)

