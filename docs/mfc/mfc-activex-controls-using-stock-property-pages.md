---
title: 'Kontrolki ActiveX MFC: Używanie stron właściwości standardowych'
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
ms.openlocfilehash: b73a027422cfe9cbf03afece400c1b513cace151
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304707"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Kontrolki ActiveX MFC: Używanie stron właściwości standardowych

W tym artykule omówiono dostępne dla formantów ActiveX i sposobu ich używania stron właściwości standardowych.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

Aby uzyskać więcej informacji na temat używania stron właściwości w kontrolce ActiveX zobacz następujące artykuły:

- [Kontrolki ActiveX MFC: Strony właściwości](../mfc/mfc-activex-controls-property-pages.md)

- [Kontrolki ActiveX MFC: Dodawanie innego niestandardowej strony właściwości](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

Biblioteka MFC zawiera trzy strony właściwości podstawowych do użytku z kontrolek ActiveX: `CLSID_CColorPropPage`, `CLSID_CFontPropPage`, i `CLSID_CPicturePropPage`. Interfejs użytkownika dla standardowych kolor, czcionki i właściwości obrazu, na tych stronach są wyświetlane w odpowiednio.

Aby dołączyć te strony właściwości do kontrolki, należy dodać ich identyfikatorów do kodu, który inicjuje tablica identyfikatory stron właściwości formantu. W poniższym przykładzie, ten kod znajduje się w pliku implementacji (. CPP) inicjuje tablicy ma zawierać wszystkie trzy strony właściwości podstawowych i domyślna strona właściwości (o nazwie `CMyPropPage` w tym przykładzie):

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Należy pamiętać, że liczba stron właściwości w BEGIN_PROPPAGEIDS — makro, to 4. Reprezentuje liczbę stron właściwości jest obsługiwana przez kontrolkę ActiveX.

Po dokonaniu tych modyfikacji, należy ponownie skompilować projekt. Formant ma teraz stron właściwości czcionki, zdjęcia i właściwości kolorów.

> [!NOTE]
>  Jeśli nie można uzyskać dostępu do strony właściwości podstawowych kontroli, prawdopodobnie biblioteki MFC DLL (MFCxx.DLL) nie został prawidłowo zarejestrowany z bieżącym systemem operacyjnym. Zazwyczaj wynika to z instalacji Visual C++ w obszarze system operacyjny inny niż ten, który aktualnie uruchomione.

> [!TIP]
>  Jeśli Twoje strony właściwości podstawowych nie są widoczne (patrz Uwaga poprzedniego), zarejestruj plik DLL, uruchamiając RegSvr32.exe z wiersza polecenia, za pomocą pełną nazwę ścieżki do biblioteki DLL.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: Dodawanie właściwości standardowych](../mfc/mfc-activex-controls-adding-stock-properties.md)
