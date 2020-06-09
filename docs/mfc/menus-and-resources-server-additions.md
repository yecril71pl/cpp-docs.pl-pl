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
ms.openlocfilehash: f67212dc7d4e2ab90421c7b2eee48acae4745940
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626182"
---
# <a name="menus-and-resources-server-additions"></a>Menu i zasoby: dodatki do serwera

W tym artykule opisano zmiany, które należy wykonać w menu i innych zasobach w aplikacji serwerowej edycji wizualnej (składnik). Aplikacja serwera wymaga wielu dodatków do struktury menu i innych zasobów, ponieważ można ją uruchomić w jednym z trzech trybów: autonomiczny, osadzony lub w miejscu. Zgodnie z opisem w artykule [menu i zasoby (OLE)](menus-and-resources-ole.md) istnieje maksymalnie cztery zestawy menu. Wszystkie cztery są używane dla aplikacji pełnego serwera MDI, ale tylko trzy są używane dla miniserver. Kreator aplikacji utworzy układ menu niezbędny dla żądanego typu serwera. Może być konieczne pewne dostosowanie.

Jeśli nie używasz Kreatora aplikacji, możesz chcieć przyjrzeć się HIERSVR. RC, skrypt zasobów dla przykładowej aplikacji MFC [HIERSVR](../overview/visual-cpp-samples.md), aby zobaczyć, jak te zmiany są implementowane.

Tematy omówione w tym artykule obejmują:

- [Dodatki do menu serwera](#_core_server_menu_additions)

- [Dodatki do tabeli akceleratora](#_core_server_application_accelerator_table_additions)

- [Dodatki do tabeli ciągów](menus-and-resources-container-additions.md)

- [Miniserver Dodatki](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>Dodatki do menu serwera

Aplikacje serwerowe (składniki) muszą mieć dodane zasoby menu do obsługi edycji wizualizacji OLE. Menu używane, gdy aplikacja jest uruchamiana w trybie autonomicznym, nie trzeba zmieniać, ale należy dodać dwa nowe zasoby menu przed skompilowaniem aplikacji: jeden do obsługi aktywacji w miejscu i jeden do obsługi całkowicie otwartego serwera. Oba zasoby menu są używane przez aplikacje pełne i miniserver.

- Aby zapewnić obsługę aktywacji w miejscu, należy utworzyć zasób menu, który jest bardzo podobny do zasobu menu używanego podczas uruchamiania w trybie autonomicznym. Różnica w tym menu polega na tym, że brakuje plików i elementów okna (i innych elementów menu związanych z aplikacją, a nie danych). Aplikacja kontenera dostarczy te elementy menu. Aby uzyskać więcej informacji na temat i przykład tej techniki łączenia menu, zobacz menu artykuł [i zasoby: scalanie menu](menus-and-resources-menu-merging.md).

- Aby zapewnić obsługę w pełni otwartej aktywacji, należy utworzyć zasób menu niemal identyczny z zasobem menu używanym podczas uruchamiania w trybie autonomicznym. Jedyną modyfikacją tego zasobu menu jest to, że niektóre elementy są uwzględniane w celu odzwierciedlenia faktu, że serwer działa na elemencie osadzonym w dokumencie złożonym.

Poza zmianami wymienionymi w tym artykule, plik zasobów musi zawierać AFXOLESV. RC, który jest wymagany dla implementacji biblioteka MFC. Ten plik znajduje się w podkatalogu MFC\Include.

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>Dodatki tabeli akceleratora aplikacji serwera

Do aplikacji serwera należy dodać dwa nowe zasoby tabeli akceleratorów. są one zgodne bezpośrednio z wcześniej opisanymi nowymi zasobami menu. Pierwsza tabela akceleratorów jest używana po aktywowaniu aplikacji serwera. Składa się ze wszystkich wpisów w tabeli akceleratorów widoku, z wyjątkiem tych, które są powiązane z menu plik i okno.

Druga tabela jest niemal dokładną kopią tabeli akceleratora widoku. Wszelkie różnice między zmianami, które zostały wprowadzone w całkowicie otwartym menu wymienionym w [dodatkach menu serwer](#_core_server_menu_additions).

Aby zapoznać się z przykładem zmian w tabeli akceleratorów, należy porównać tabele IDR_HIERSVRTYPE_SRVR_IP i akceleratora IDR_HIERSVRTYPE_SRVR_EMB z IDR_MAINFRAME w HIERSVR. Plik RC dołączony do przykładu OLE MFC [HIERSVR](../overview/visual-cpp-samples.md). W tabeli w miejscu brakuje akceleratorów plików i okien i ich dokładne kopie znajdują się w osadzonej tabeli.

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>Dodatki do tabeli ciągów dla aplikacji serwerowych

W aplikacji serwera jest wymagana tylko jedna tabela ciągów — ciąg, który oznacza, że inicjowanie OLE nie powiodło się. Poniżej znajduje się przykład wpisu tabeli ciągów, który generuje Kreator aplikacji:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Inicjowanie OLE nie powiodło się. Upewnij się, że biblioteki OLE są w poprawnej wersji.|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>Miniserver Dodatki

Te same dodatki dotyczą miniservers jak te wymienione powyżej dla całego serwera. Ponieważ nie można uruchomić miniserver w trybie autonomicznym, jego menu główne jest dużo mniejsze. Menu główne utworzone przez Kreatora aplikacji ma tylko menu plik zawierające tylko te elementy. Wbudowane i wbudowane menu i akceleratory dla miniservers są takie same jak dla wszystkich serwerów.

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](menus-and-resources-ole.md)<br/>
[Menu i zasoby: scalanie menu](menus-and-resources-menu-merging.md)
