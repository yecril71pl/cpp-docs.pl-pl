---
title: 'Formanty MFC ActiveX: lokalizowanie formantu ActiveX'
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: 987cde2117307cdb5940a31e6f01efb15c527b84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364596"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Formanty MFC ActiveX: lokalizowanie formantu ActiveX

W tym artykule omówiono procedury lokalizowania interfejsów sterowania ActiveX.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Jeśli chcesz dostosować formant ActiveX do rynku międzynarodowego, możesz zlokalizować formant. System Windows obsługuje wiele języków oprócz domyślnego języka angielskiego, w tym niemieckiego, francuskiego i szwedzkiego. Może to stwarzać problemy dla formantu, jeśli jego interfejs jest tylko w języku angielskim.

Ogólnie rzecz biorąc formanty ActiveX powinny zawsze opierać swoje ustawienia regionalne na właściwość otoczenia LocaleID. Można to zrobić na trzy sposoby:

- Załaduj zasoby, zawsze na żądanie, na podstawie bieżącej wartości właściwości LocaleID otoczenia. Przykładowe formanty MFC ActiveX [LOCALIZE](../overview/visual-cpp-samples.md) używa tej strategii.

- Załaduj zasoby, gdy wystąpi ą pierwsze formanty, na podstawie właściwości LocaleID otoczenia i użyj tych zasobów dla wszystkich innych wystąpień. W tym artykule przedstawiono tę strategię.

    > [!NOTE]
    >  To nie będzie działać poprawnie w niektórych przypadkach, jeśli przyszłe wystąpienia mają różne ustawienia regionalne.

- Funkcja `OnAmbientChanged` powiadomień umożliwia dynamiczne ładowanie odpowiednich zasobów dla ustawień regionalnych kontenera.

    > [!NOTE]
    >  Będzie to działać dla formantu, ale biblioteka DLL w czasie wykonywania nie będzie dynamicznie aktualizować własne zasoby po zmianie właściwości localeID otoczenia. Ponadto biblioteki DLL w czasie wykonywania dla formantów ActiveX używają ustawień regionalnych wątku do określenia ustawień regionalnych dla swoich zasobów.

W dalszej części tego artykułu opisano dwie strategie lokalizacji. Pierwsza strategia [lokalizuje interfejs programowania formantu](#_core_localizing_your_control.92.s_programmability_interface) (nazwy właściwości, metody i zdarzenia). Druga strategia [lokalizuje interfejs użytkownika formantu](#_core_localizing_the_control.92.s_user_interface), przy użyciu właściwości LocaleID kontenera. Aby zapoznać się z demonstracją lokalizacji sterowania, zobacz przykład kontrolek MFC ActiveX [LOCALIZE](../overview/visual-cpp-samples.md).

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a>Lokalizowanie interfejsu programowania formantu

Podczas lokalizowania interfejsu programowalności formantu (interfejsu używanego przez programistów piszących aplikacje korzystające z formantu) należy utworzyć zmodyfikowaną wersję formantu . Plik IDL (skrypt do tworzenia biblioteki typów formantów) dla każdego języka, który ma być obsługiwany. Jest to jedyne miejsce, w które należy zlokalizować nazwy właściwości formantu.

Podczas tworzenia zlokalizowanego formantu należy uwzględnić identyfikator ustawień regionalnych jako atrybut na poziomie biblioteki typów. Na przykład jeśli chcesz podać bibliotekę typów z francuskimi nazwami właściwości zlokalizowanych, należy wykonać kopię przykładu. IDL i wywołać go SAMPLEFR. Idl. Dodaj atrybut identyfikatora ustawień regionalnych do pliku (identyfikator ustawień regionalnych dla języka francuskiego to 0x040c), podobny do następującego:

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Zmień nazwy właściwości w SAMPLEFR. IDL do ich francuskich odpowiedników, a następnie użyj MKTYPLIB. EXE do produkcji biblioteki typów francuskich, SAMPLEFR. Tlb.

Aby utworzyć wiele zlokalizowanych bibliotek typów, można dodać dowolny zlokalizowany plik . IDL plików do projektu i zostaną one utworzone automatycznie.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Aby dodać plik . IDL do projektu sterowania ActiveX

1. Po otwarciu projektu sterującego w menu **Projekt** kliknij polecenie **Dodaj istniejący element**.

   Zostanie wyświetlone okno dialogowe **Dodawanie istniejącego elementu.**

1. W razie potrzeby wybierz dysk i katalog do wyświetlenia.

1. W polu **Pliki typu** wybierz pozycję Wszystkie pliki **(\*\*. )**.

1. W polu listy plików kliknij dwukrotnie przycisk . Plik IDL, który chcesz wstawić do projektu.

1. Kliknij **przycisk Otwórz** po dodaniu wszystkich niezbędnych . idl.

Ponieważ pliki zostały dodane do projektu, zostaną one utworzone podczas budowy pozostałej części projektu. Zlokalizowane biblioteki typów znajdują się w bieżącym katalogu projektów sterowania ActiveX.

W kodzie nazwy właściwości wewnętrznych (zwykle w języku angielskim) są zawsze używane i nigdy nie są zlokalizowane. Obejmuje to mapę wysyłki kontroli, funkcje wymiany właściwości i kod wymiany danych strony właściwości.

Tylko jedna biblioteka typów (. TLB) może być powiązany z zasobami implementacji kontroli (. OCX). Zazwyczaj jest to wersja ze standardowymi (zazwyczaj angielskimi) nazwami. Aby wysłać zlokalizowaną wersję formantu, musisz wysłać plik . OCX (który został już powiązany z wartością domyślną . wersji TLB) oraz . TLB dla odpowiednich ustawień regionalnych. Oznacza to, że tylko . OCX jest potrzebne w wersjach angielskich, ponieważ poprawne . TLB został już z nim powiązany. W przypadku innych ustawień regionalnych zlokalizowana biblioteka typów również musi być dostarczona z programem . Ocx.

Aby upewnić się, że klienci formantu mogą znaleźć zlokalizowaną bibliotekę typów, zarejestruj ustawienia regionalne. W sekcji TypeLib rejestru systemu Windows. Trzeci parametr (zwykle opcjonalny) funkcji [AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) jest w tym celu podany. Poniższy przykład rejestruje bibliotekę typów francuskich dla formantu ActiveX:

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Po zarejestrowaniu formantu `AfxOleRegisterTypeLib` funkcja automatycznie wyszukuje określony plik . TLB w tym samym katalogu co formant i rejestruje go w bazie danych rejestracji systemu Windows. Jeśli plik . Nie znaleziono pliku TLB, funkcja nie ma wpływu.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a>Lokalizowanie interfejsu użytkownika formantu

Aby zlokalizować interfejs użytkownika formantu, umieść wszystkie zasoby widoczne dla użytkownika (takie jak strony właściwości i komunikaty o błędach) na biblioteki DLL zasobów specyficzne dla języka. Następnie można użyć właściwości LocaleID kontenera, aby wybrać odpowiednią bibliotekę DLL dla ustawień regionalnych użytkownika.

Poniższy przykład kodu pokazuje jedno podejście, aby zlokalizować i załadować bibliotekę DLL zasobu dla określonych ustawień regionalnych. Ta funkcja elementu `GetLocalizedResourceHandle` członkowskiego, wywoływana w tym przykładzie, może być funkcją członkowną klasy sterowania ActiveX:

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Należy zauważyć, że identyfikator podjęzyku można sprawdzić w każdym przypadku instrukcji switch, aby zapewnić bardziej wyspecjalizowaną lokalizację. Aby zapoznać się z `GetResourceHandle` demonstracją tej funkcji, zobacz funkcję w przykładzie formantów MFC ActiveX [LOCALIZE](../overview/visual-cpp-samples.md).

Gdy formant najpierw ładuje się do kontenera, można wywołać [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) pobrać identyfikator ustawień regionalnych. Formant może następnie przekazać zwróconą wartość `GetLocalizedResourceHandle` identyfikatora ustawień regionalnych do funkcji, która ładuje właściwą bibliotekę zasobów. Formant powinien przekazać wynikowy uchwyt, jeśli istnieje, do [AfxSetResourceHandle:](../mfc/reference/application-information-and-management.md#afxsetresourcehandle)

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Umieść przykładowy kod powyżej w funkcji elementu członkowskiego formantu, takiej jak zastąpienie [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Ponadto *m_hResDLL* powinna być zmienną elementu członkowskiego klasy kontrolnej.

Podobną logikę można użyć do lokalizowania strony właściwości formantu. Aby zlokalizować stronę właściwości, dodaj kod podobny do następującego przykładu do pliku implementacji strony właściwości (w zastąpieniu [COlePropertyPage::OnSetPageSite):](../mfc/reference/colepropertypage-class.md#onsetpagesite)

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
