---
title: 'TN023: Standardowe zasoby MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.resources
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: d29f0ab2254a52e01f2016f64a37ddfce47955bb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780317"
---
# <a name="tn023-standard-mfc-resources"></a>TN023: Standardowe zasoby MFC

Ta uwaga opisuje standardowe zasoby dostarczany z usługą i wymagane przez bibliotekę MFC.

## <a name="standard-resources"></a>Standardowe zasoby

MFC udostępnia dwie kategorie wstępnie zdefiniowanych zasobów, które można użyć w aplikacji: zasoby pozyskiwać i standardowych zasobów RAM.

Obiekty clipart zasoby są dodatkowe zasoby, w ramach nie zależy od, ale które możesz zechcieć dodać do interfejsu użytkownika aplikacji. W następujących zasobach pozyskiwać są zawarte w próbki MFC-ogólne [CLIPART](../overview/visual-cpp-samples.md):

- Common.RC: Pojedynczego pliku zasobów zawierającego:

   - Duża kolekcja ikon reprezentujących różne zadania przetwarzania danych i biznesowych.

   - Kilka typowych kursorów (Zobacz również plik Afxres.rc).

   - Mapę bitową do paska narzędzi, który zawiera kilka przycisków paska narzędzi.

   - Zasoby bitmap i ikon, które są używane przez Commdlg.dll.

- Indicate.RC: Zawiera zasoby ciągów dla wskaźników klucz stanu paska stanu, takie jak "Limit", aby uzyskać włączony klawisz Caps Lock.

- Prompts.RC: Id_file_new — zawiera zasoby w postaci ciągów menu wiersza dla każdego polecenia wstępnie zdefiniowanych, takie jak "Utwórz nowy dokument".

- COMMDLG.RC: Plik .rc zgodne Visual C++, który zawiera standardowych szablonów pliku COMMDLG w oknie dialogowym.

Standardowych zasobów RAM są zasobami za pomocą identyfikatorów zdefiniowanych AFX ramach zależy od wewnętrznej implementacji. Rzadko należy zmieniać te zasoby zdefiniowane AFX. Jeśli to zrobisz, należy wykonać procedury opisane w dalszej części tego tematu.

Następujące zasoby struktury są zawarte w katalogu MFC\INCLUDE:

- Pliki Afxres.RC: Typowe zasoby używane przez platformę.

- Afxprint.RC: Zasoby specyficzne dla drukowania.

- Afxolecl.RC: Zasoby specyficzne dla aplikacji klienckich OLE.

- Afxolev.RC: Zasoby specyficzne dla pełnego aplikacje serwera OLE.

## <a name="using-clip-art-resources"></a>Korzystanie z zasobów obiekty clipart

#### <a name="to-use-a-clip-art-binary-resource"></a>Aby użyć zasób binarny obiekty clipart

1. Otwórz plik zasobów aplikacji w języku Visual C++.

1. Open Common.rc. Ten plik zawiera wszystkie zasoby binarne clipart. To może potrwać pewien czas, ponieważ plik Common.rc został skompilowany.

1. Przytrzymaj klawisz CTRL podczas przeciągania zasoby, które mają używać ze Common.rc do pliku zasobów aplikacji.

Aby korzystać z innych zasobów pozyskiwać, wykonaj te same czynności. Jedyna różnica polega na tym, czy zostanie otwarty plik .rc odpowiednie zamiast Common.rc.

> [!NOTE]
>  Uważaj, aby nie przypadkowo trwałe przeniesienie zasobów poza Common.rc. Przytrzymując klawisz CTRL podczas przeciągania zasobów, spowoduje utworzenie kopii. Jeśli możesz nie przytrzymaj klawisz CTRL podczas przeciągania, zasoby zostaną przeniesione. Jeśli dane, może przypadkowo wprowadzone zmiany do pliku Common.rc, kliknij przycisk "No", gdy zostanie wyświetlony monit, czy chcesz zapisać zmiany dotyczące operacji Common.rc.

> [!NOTE]
>  Pliki zasobów .rc mają specjalne zasób TEXTINCLUDE w nich, które uniemożliwiają przypadkowo zapisywania na podstawie plików standard .rc.

### <a name="customizing-standard-framework-resources"></a>Dostosowywanie standardowych zasobów RAM

Standardowych zasobów RAM zwykle znajdują się w aplikacji przy użyciu #include polecenia Plik zasobów aplikacji. Kreator AppWizard wygeneruje plik zasobów. Ten plik zawiera odpowiednie standardowych zasobów RAM, zależności od tego, jakie opcje przez kreatora AppWizard wybierz. Można przejrzeć, Dodaj lub Usuń, które zasoby znajdują się przez zmianę w dyrektywach czasu kompilacji. Aby to zrobić, otwórz **zasobów** menu, a następnie wybierz **zestaw zawiera**. Spójrz na edytowanie elementu "Dyrektywy czasu kompilacji". Na przykład:

```
#include "afxres.rc"
#include "afxprint.rc"
```

Najbardziej typowe w przypadku dostosowywanie standardowych zasobów RAM jest dodawanie lub usuwanie dodatkowych obejmuje związane z drukowaniem, klienta OLE i pomoc techniczna dotycząca serwera OLE.

W rzadkich przypadkach możesz chcieć dostosować zawartość standardowych zasobów ram dla określonej aplikacji nie tylko dodawać i usuwać całego pliku. Kroki w następujących tematach przedstawiają sposób ograniczenia zasobów, które są dołączone:

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Aby dostosować zawartość pliku standardowych zasobów

1. Otwórz plik zasobów w programie Visual C++.

1. Za pomocą polecenia zestaw zasobów zawiera Usuń `#include` dla pliku .rc standardowa, który chcesz dostosować. Na przykład Dostosowywanie paska narzędzi podglądu wydruku, usunąć `#include "afxprint.rc"` wiersza.

1. Otwórz pliki odpowiednie standardowe zasoby w MFC\INCLUDE. Następujący przykład we wcześniejszej części tego tematu odpowiedniego pliku jest MFC\Include\Aafxprint.rc

1. Skopiuj wszystkie zasoby z pliku .rc standardowy do Twojego pliku zasobu aplikacji.

1. Zmodyfikuj kopię standardowe zasoby w pliku zasobów aplikacji.

> [!NOTE]
>  Nie należy modyfikować zasobów bezpośrednio w plikach .rc standardowych. Ten sposób zmodyfikuje zasoby dostępne w każdej aplikacji, a nie tylko w jeden, w którym aktualnie pracuje.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
