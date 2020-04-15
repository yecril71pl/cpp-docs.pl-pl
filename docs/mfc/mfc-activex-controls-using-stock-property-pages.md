---
title: 'Kontrolki ActiveX MFC: używanie stron właściwości standardowych'
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
ms.openlocfilehash: 13a0edb72657c9ffad00dcb909019bdfe4b87e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358193"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Kontrolki ActiveX MFC: używanie stron właściwości standardowych

W tym artykule omówiono strony właściwości giełdowych dostępne dla formantów ActiveX i sposób ich używania.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Aby uzyskać więcej informacji na temat używania stron właściwości w formancie ActiveX, zobacz następujące artykuły:

- [Kontrolki ActiveX MFC: strony właściwości](../mfc/mfc-activex-controls-property-pages.md)

- [Formanty MFC ActiveX: dodawanie dodatkowej niestandardowej strony właściwości](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

MFC udostępnia trzy strony właściwości giełdowych `CLSID_CColorPropPage`do `CLSID_CFontPropPage`użytku `CLSID_CPicturePropPage`z formantami ActiveX: , , i . Te strony wyświetlają interfejs użytkownika dla koloru zapasów, czcionki i właściwości obrazu, odpowiednio.

Aby włączyć te strony właściwości do formantu, dodaj ich identyfikatory do kodu, który inicjuje tablicę identyfikatorów stron właściwości formantu. W poniższym przykładzie ten kod, znajdujący się w pliku implementacji formantu (. CPP), inicjuje tablicę zawierającą wszystkie trzy strony właściwości `CMyPropPage` magazynowych i domyślną stronę właściwości (nazwaną w tym przykładzie):

[!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Należy zauważyć, że liczba stron właściwości w BEGIN_PROPPAGEIDS makra wynosi 4. Reprezentuje liczbę stron właściwości obsługiwanych przez formant ActiveX.

Po dokonaniu tych modyfikacji odbuduj projekt. Formant ma teraz strony właściwości dla właściwości czcionki, obrazu i koloru.

> [!NOTE]
> Jeśli nie można uzyskać dostępu do stron właściwości zapasów formantu, może to być spowodowane tym, że biblioteka DLL MFC (MFCxx.DLL) nie została poprawnie zarejestrowana w bieżącym systemie operacyjnym. Zwykle wynika to z instalacji języka Visual C++ w systemie operacyjnym innym niż obecnie uruchomiony.

> [!TIP]
> Jeśli strony właściwości magazynu nie są widoczne (patrz poprzednia uwaga), zarejestruj bibliotekę DLL, uruchamiając plik RegSvr32.exe z wiersza polecenia z pełną nazwą ścieżki do biblioteki DLL.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: dodawanie właściwości standardowych](../mfc/mfc-activex-controls-adding-stock-properties.md)
