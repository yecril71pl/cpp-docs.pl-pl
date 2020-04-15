---
title: Implementowanie okna z CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: e5fdbf15ddd7edc69f0667a9b7e08c7c5e531a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319447"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementowanie okna z CWindowImpl

Aby zaimplementować okno, `CWindowImpl`wywodź klasę z . W klasie pochodnej zadeklarować mapę wiadomości i funkcje obsługi wiadomości. Teraz możesz używać swojej klasy na trzy różne sposoby:

- [Tworzenie okna na podstawie nowej klasy systemu Windows](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Nadklasy istniejącej klasy systemu Windows](#_atl_superclassing_an_existing_windows_class)

- [Podklasa istniejącego okna](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>Tworzenie okna na podstawie nowej klasy systemu Windows

`CWindowImpl`zawiera [makro DECLARE_WND_CLASS,](reference/window-class-macros.md#declare_wnd_class) aby zadeklarować informacje o klasie systemu Windows. To makro implementuje `GetWndClassInfo` funkcję, która używa [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) do definiowania informacji o nowej klasie systemu Windows. Po `CWindowImpl::Create` wywołaniu ta klasa systemu Windows jest zarejestrowana i tworzone jest nowe okno.

> [!NOTE]
> `CWindowImpl`przekazuje wartość `DECLARE_WND_CLASS` NULL do makra, co oznacza, że ATL wygeneruje nazwę klasy systemu Windows. Aby określić własną nazwę, przekaż ciąg do `CWindowImpl`DECLARE_WND_CLASS w klasie pochodnej.

## <a name="example"></a>Przykład

Oto przykład klasy, która implementuje okno oparte na nowej klasie systemu Windows:

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Aby utworzyć okno, utwórz `CMyWindow` wystąpienie, `Create` a następnie wywołaj metodę.

> [!NOTE]
> Aby zastąpić domyślne informacje o klasie `GetWndClassInfo` systemu Windows, należy zaimplementować metodę w klasie pochodnej, ustawiając `CWndClassInfo` elementy członkowskie na odpowiednie wartości.

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a>Przeklasyfikowanie istniejącej klasy systemu Windows

Makro [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) umożliwia utworzenie okna, które naklasuje istniejącą klasę systemu Windows. Określ to `CWindowImpl`makro w klasie pochodnej. Jak każde inne okno ATL, wiadomości są obsługiwane przez mapę wiadomości.

Podczas korzystania z DECLARE_WND_SUPERCLASS zostanie zarejestrowana nowa klasa systemu Windows. Ta nowa klasa będzie taka sama jak istniejąca klasa, którą `CWindowImpl::WindowProc` określisz, ale zastąpi procedurę okna (lub funkcją, która zastępuje tę metodę).

## <a name="example"></a>Przykład

Poniżej przedstawiono przykład klasy, która superclasses standardowej Edit klasy:

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Aby utworzyć okno edycji superklasyfikowane, utwórz wystąpienie, `CMyEdit` a następnie wywołaj `Create` metodę.

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a>Podklasy istniejącego okna

Aby podklasy istniejącego okna, `CWindowImpl` wyprowadzić klasę z i zadeklarować mapę wiadomości, jak w dwóch poprzednich przypadkach. Należy jednak pamiętać, że nie należy określać żadnych informacji o klasie systemu Windows, ponieważ będzie podklasa już istniejące okno.

Zamiast wywoływać `Create`, `SubclassWindow` wywołać i przekazać go dojście do istniejącego okna, które chcesz podklasy. Gdy okno jest podklasyfikowane, użyje `CWindowImpl::WindowProc` (lub funkcji, która zastępuje tę metodę) do bezpośredniego wiadomości do mapy wiadomości. Aby odłączyć okno podklasy `UnsubclassWindow`od obiektu, wywołaj polecenie . Następnie zostanie przywrócona oryginalna procedura okna okna.

## <a name="see-also"></a>Zobacz też

[Implementowanie okna](../atl/implementing-a-window.md)
