---
title: Wirtualne formanty listy
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 1ade5f404e134cf6de20756dcc5af169fefdec76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375512"
---
# <a name="virtual-list-controls"></a>Wirtualne formanty listy

Formant listy wirtualnej jest formantem widoku listy, który ma styl LVS_OWNERDATA. Ten styl umożliwia formancie obsługę liczby elementów do **DWORD** (domyślna liczba elementów rozciąga się tylko na **int**). Jednak największą zaletą tego stylu jest możliwość mieć tylko podzbiór elementów danych w pamięci w dowolnym momencie. Dzięki temu formant widoku listy wirtualnej nadaje się do użytku z dużymi bazami danych informacji, gdzie określone metody uzyskiwania dostępu do danych są już na miejscu.

> [!NOTE]
> Oprócz zapewnienia funkcji listy wirtualnej w `CListCtrl`, MFC zapewnia również taką samą funkcjonalność w [CListView](../mfc/reference/clistview-class.md) klasy.

Istnieją pewne problemy ze zgodnością, o których należy pamiętać podczas tworzenia formantów listy wirtualnej. Aby uzyskać więcej informacji, zobacz sekcję Problemy ze zgodnością w temacie Formanty widoku listy w zestawie Windows SDK.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Obsługa powiadomienia LVN_GETDISPINFO

Kontrolki listy wirtualnej zachowują bardzo mało informacji o elemencie. Z wyjątkiem informacji o wyborze elementu i fokusie, wszystkie informacje o elemencie są zarządzane przez właściciela formantu. Informacje są wymagane przez ramy za pośrednictwem komunikatu o LVN_GETDISPINFO powiadomieniu. Aby dostarczyć żądanych informacji, właściciel formantu listy wirtualnej (lub samego formantu) musi obsłużyć to powiadomienie. Można to łatwo zrobić za pomocą [Kreatora klas](reference/mfc-class-wizard.md) (zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Wynikowy kod powinien wyglądać mniej więcej `CMyDialog` jak w poniższym przykładzie (gdzie jest właścicielem obiektu kontroli listy wirtualnej, a okno dialogowe obsługuje powiadomienie):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

W programie obsługi komunikatu powiadomienia LVN_GETDISPINFO należy sprawdzić, jaki typ informacji jest wymagane. Możliwe wartości są następujące:

- `LVIF_TEXT`Element członkowski *pszText* musi zostać wypełniony.

- `LVIF_IMAGE`Element członkowski *iImage* musi być wypełniony.

- `LVIF_INDENT`Element *członkowski iIndent* musi być wypełniony.

- `LVIF_PARAM`Element członkowski *lParam* musi być wypełniony. (Nie występuje dla podudziałów.)

- `LVIF_STATE`Członek *państwa* musi być wypełniony.

Następnie należy podać wszelkie informacje wymagane z powrotem do struktury.

Poniższy przykład (zaczerpnięty z treści programu obsługi powiadomień dla obiektu kontroli listy) pokazuje jedną z możliwych metod, dostarczając informacje dla buforów tekstowych i obrazu elementu:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Sterowanie buforowaniem i wirtualną listą

Ponieważ ten typ formantu listy jest przeznaczony dla dużych zestawów danych, zaleca się buforowanie żądanych danych elementu w celu zwiększenia wydajności pobierania. Struktura zapewnia mechanizm podpowiedzi pamięci podręcznej, aby pomóc w optymalizacji pamięci podręcznej, wysyłając komunikat powiadomienia LVN_ODCACHEHINT.

Poniższy przykład aktualizuje pamięci podręcznej z zakresu przekazywane do funkcji obsługi.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Aby uzyskać więcej informacji na temat przygotowywania i utrzymywania pamięci podręcznej, zobacz sekcję Zarządzanie pamięcią podręczną w temacie Formanty widoku listy w zestawie Windows SDK.

## <a name="finding-specific-items"></a>Znajdowanie określonych elementów

Komunikat powiadomienia LVN_ODFINDITEM jest wysyłany przez formant listy wirtualnej, gdy należy znaleźć określony element kontroli listy. Wiadomość powiadomienia jest wysyłana, gdy kontrolka widoku listy odbiera szybki dostęp do kluczy lub gdy odbiera wiadomość LVM_FINDITEM. Informacje wyszukiwania są wysyłane w formie struktury **LVFINDINFO,** która jest członkiem struktury **NMLVFINDITEM.** Obsługa tego komunikatu `OnChildNotify` przez zastąpienie funkcji obiektu kontroli listy i wewnątrz treści programu obsługi, sprawdź, LVN_ODFINDITEM komunikat. Jeśli zostanie znaleziony, wykonaj odpowiednią akcję.

Należy przygotować się do wyszukiwania elementu, który pasuje do informacji podanych przez formant widoku listy. Należy zwrócić indeks towaru, jeśli zakończy się pomyślnie, lub -1, jeśli nie znaleziono pasującego elementu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
