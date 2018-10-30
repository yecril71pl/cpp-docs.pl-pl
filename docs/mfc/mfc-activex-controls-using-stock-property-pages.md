---
title: 'Kontrolki ActiveX MFC: Używanie stron właściwości standardowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc7957e69821a409d5ad56bd10c222cbe85fbc54
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204408"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Kontrolki ActiveX MFC: używanie stron właściwości standardowych

W tym artykule omówiono dostępne dla formantów ActiveX i sposobu ich używania stron właściwości standardowych.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

Aby uzyskać więcej informacji na temat używania stron właściwości w kontrolce ActiveX zobacz następujące artykuły:

- [Kontrolki ActiveX MFC: strony właściwości](../mfc/mfc-activex-controls-property-pages.md)

- [Kontrolki ActiveX MFC: dodawanie dodatkowej niestandardowej strony właściwości](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

Biblioteka MFC zawiera trzy strony właściwości podstawowych do użytku z kontrolek ActiveX: `CLSID_CColorPropPage`, `CLSID_CFontPropPage`, i `CLSID_CPicturePropPage`. Interfejs użytkownika dla standardowych kolor, czcionki i właściwości obrazu, na tych stronach są wyświetlane w odpowiednio.

Aby dołączyć te strony właściwości do kontrolki, należy dodać ich identyfikatorów do kodu, który inicjuje tablica identyfikatory stron właściwości formantu. W poniższym przykładzie, ten kod znajduje się w pliku implementacji (. CPP) inicjuje tablicy ma zawierać wszystkie trzy strony właściwości podstawowych i domyślna strona właściwości (o nazwie `CMyPropPage` w tym przykładzie):

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Należy pamiętać, że liczba stron właściwości w BEGIN_PROPPAGEIDS — makro, to 4. Reprezentuje liczbę stron właściwości jest obsługiwana przez kontrolkę ActiveX.

Po dokonaniu tych modyfikacji, należy ponownie skompilować projekt. Formant ma teraz stron właściwości czcionki, zdjęcia i właściwości kolorów.

> [!NOTE]
>  Jeśli nie można uzyskać dostępu do strony właściwości podstawowych kontroli, prawdopodobnie biblioteki MFC DLL (MFCxx.DLL) nie został prawidłowo zarejestrowany z bieżącym systemem operacyjnym. Zazwyczaj wynika to z instalacji Visual C++ w obszarze system operacyjny inny niż ten, który aktualnie uruchomione.

> [!TIP]
>  Jeśli Twoje strony właściwości podstawowych nie są widoczne (patrz Uwaga poprzedniego), zarejestruj plik DLL, uruchamiając RegSvr32.exe z wiersza polecenia, za pomocą pełną nazwę ścieżki do biblioteki DLL.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: dodawanie właściwości standardowych](../mfc/mfc-activex-controls-adding-stock-properties.md)

