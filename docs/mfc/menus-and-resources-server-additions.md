---
title: 'Menu i zasoby: dodatki do serwera'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
ms.openlocfilehash: 8366cd8b0376766b7914c94a24cef6598761a805
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375988"
---
# <a name="menus-and-resources-server-additions"></a>Menu i zasoby: dodatki do serwera

W tym artykule opisano zmiany, które należy włożyć do menu i innych zasobów w wizualnej edycji serwera (składnika) aplikacji. Aplikacja serwera wymaga wielu dodatków do struktury menu i innych zasobów, ponieważ można ją uruchomić w jednym z trzech trybów: autonomicznym, osadzonym lub w miejscu. Zgodnie z opisem w [menu i zasobów (OLE)](../mfc/menus-and-resources-ole.md) artykuł, istnieją maksymalnie cztery zestawy menu. Wszystkie cztery są używane dla aplikacji mdi pełnego serwera, podczas gdy tylko trzy są używane dla miniserweru. Kreator aplikacji utworzy układ menu niezbędny dla odpowiedniego typu serwera. Niektóre dostosowania mogą być konieczne.

Jeśli nie używasz kreatora aplikacji, możesz chcieć przyjrzeć się HIERSVR. RC, skrypt zasobów dla przykładowej aplikacji MFC [HIERSVR](../overview/visual-cpp-samples.md), aby zobaczyć, jak te zmiany są implementowane.

Tematy omówione w tym artykule obejmują:

- [Dodatki do menu serwera](#_core_server_menu_additions)

- [Dodatki tabeli akceleratora](#_core_server_application_accelerator_table_additions)

- [Dodatki do tabel ciągów](../mfc/menus-and-resources-container-additions.md)

- [Dodatki do miniserweru](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>Dodatki do menu serwera

Aplikacje serwera (składnika) muszą mieć dodane zasoby menu do obsługi edycji wizualnej OLE. Menu używane, gdy aplikacja jest uruchamiana w trybie autonomicznym nie muszą być zmieniane, ale należy dodać dwa nowe zasoby menu przed tworzeniem aplikacji: jeden do obsługi aktywacji w miejscu i jeden do obsługi serwera jest w pełni otwarty. Oba zasoby menu są używane przez aplikacje full- i miniserver.

- Aby obsługiwać aktywację w miejscu, należy utworzyć zasób menu, który jest bardzo podobny do zasobu menu używanego podczas uruchamiania w trybie autonomicznym. Różnica w tym menu jest to, że plik i okno elementów (i innych elementów menu, które dotyczą aplikacji, a nie dane) brakuje. Aplikacja kontenera dostarczy te elementy menu. Aby uzyskać więcej informacji na temat i przykład tej techniki scalania menu, zobacz artykuł [Menu i zasoby: Łączenie menu](../mfc/menus-and-resources-menu-merging.md).

- Aby obsługiwać w pełni otwartą aktywację, należy utworzyć zasób menu prawie identyczny z zasobem menu używanym podczas uruchamiania w trybie autonomicznym. Jedyną modyfikacją tego zasobu menu jest to, że niektóre elementy są przeredagowane w celu odzwierciedlenia faktu, że serwer działa na elemencie osadzonym w dokumencie złożonym.

Oprócz zmian wymienionych w tym artykule, plik zasobów musi zawierać AFXOLESV. RC, który jest wymagany dla implementacji biblioteki klas programu Microsoft Foundation. Ten plik znajduje się w podkatalogu MFC\Include.

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>Dodatki tabeli akceleratora aplikacji serwera

Do aplikacji serwera należy dodać dwa nowe zasoby tabeli akceleratora; odpowiadają one bezpośrednio nowym zasobom menu opisanym wcześniej. Pierwsza tabela akceleratora jest używana, gdy aplikacja serwera jest aktywowana na miejscu. Składa się ze wszystkich wpisów w tabeli akceleratora widoku, z wyjątkiem tych powiązanych z menu Plik i Okno.

Druga tabela jest prawie dokładną kopią tabeli akceleratora widoku. Wszelkie różnice równoległe zmiany wprowadzone w menu w pełni otwarte wymienione w [Menu serwera Dodatki](#_core_server_menu_additions).

Na przykład tych zmian tabeli akceleratora porównaj tabele akceleratora IDR_HIERSVRTYPE_SRVR_IP i IDR_HIERSVRTYPE_SRVR_EMB z IDR_MAINFRAME w HIERSVR. RC zawarte w MFC OLE próbki [HIERSVR](../overview/visual-cpp-samples.md). Akceleratory Plików i okien brakuje w tabeli w miejscu, a dokładne ich kopie znajdują się w tabeli osadzonej.

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>Dodatki tabeli ciągów dla aplikacji serwerowych

Tylko jeden dodatek tabeli ciągów jest konieczne w aplikacji serwera — ciąg oznacza, że inicjowanie OLE nie powiodło się. Na przykład oto wpis tabeli ciągów, który generuje kreator aplikacji:

|ID|Ciąg|
|--------|------------|
|IDP_OLE_INIT_FAILED|Inicjowanie OLE nie powiodło się. Upewnij się, że biblioteki OLE są poprawną wersją.|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>Dodatki do miniserweru

Te same dodatki dotyczą miniserwerów, jak te wymienione powyżej dla pełnych serwerów. Ponieważ miniserweru nie można uruchomić w trybie autonomicznym, jego menu główne jest znacznie mniejsze. Menu główne utworzone przez kreatora aplikacji ma tylko menu Plik, zawierające tylko elementy Exit i About. Wbudowane i w miejscu menu i akceleratory dla miniserverów są takie same jak w przypadku serwerów pełnoserwowych.

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menu i zasoby: scalanie menu](../mfc/menus-and-resources-menu-merging.md)
