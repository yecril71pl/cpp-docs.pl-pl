---
title: 'TN023: standardowe zasoby MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: 90e7b9b7c354ba919c3dee279725b4498bea57ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370380"
---
# <a name="tn023-standard-mfc-resources"></a>TN023: standardowe zasoby MFC

W tej notatce opisano standardowe zasoby dostarczane i potrzebne biblioteki MFC.

## <a name="standard-resources"></a>Zasoby standardowe

MFC oferuje dwie kategorie wstępnie zdefiniowanych zasobów, które można użyć w aplikacji: zasoby clip-art i standardowe zasoby ramowe.

Zasoby obiektów clip-art są dodatkowe zasoby, które nie zależy od struktury, ale które można dodać do interfejsu użytkownika aplikacji. Następujące zasoby obiektów clipart znajdują się w przykładowym [clipartze MFC:](../overview/visual-cpp-samples.md)

- Common.rc: Pojedynczy plik zasobów, który zawiera:

  - Duży zbiór ikon, które reprezentują różne zadania biznesowe i przetwarzania danych.

  - Kilka wspólnych kursorów (patrz również Afxres.rc).

  - Mapa bitowa paska narzędzi zawierająca kilka przycisków paska narzędzi.

  - Zasoby bitmapowe i ikony używane przez plik Commdlg.dll.

- Indicate.rc: Zawiera zasoby ciągów dla wskaźników stanu-bar key-state, takich jak "CAP" dla Caps Lock.

- Prompts.rc: Zawiera zasoby ciągu monitu menu dla każdego wstępnie zdefiniowanego polecenia, takie jak "Utwórz nowy dokument" dla ID_FILE_NEW.

- Commdlg.rc: Plik .rc zgodny z programem Visual C++, który zawiera standardowe szablony dialogów COMMDLG.

Standardowe zasoby struktury są zasoby z AFX zdefiniowane identyfikatory, które zależy od struktury dla implementacji wewnętrznych. Rzadko trzeba będzie zmienić te zasoby zdefiniowane przez AFX. Jeśli to zrobisz, należy postępować zgodnie z procedurą opisaną w dalszej części tego tematu.

Następujące zasoby struktury są zawarte w katalogu MFC\INCLUDE:

- Afxres.rc: Wspólne zasoby używane przez ramy.

- Afxprint.rc: Zasoby specyficzne dla drukowania.

- Afxolecl.rc: Zasoby specyficzne dla aplikacji klienckich OLE.

- Afxolev.rc: Zasoby specyficzne dla pełnych aplikacji serwera OLE.

## <a name="using-clip-art-resources"></a>Korzystanie z zasobów obiektów clipart

#### <a name="to-use-a-clip-art-binary-resource"></a>Aby użyć zasobu binarnego obiektu clipart

1. Otwórz plik zasobów aplikacji w języku Visual C++.

1. Otwórz Common.rc. Ten plik zawiera wszystkie binarne zasoby clip-art. Może to zająć trochę czasu, ponieważ plik Common.rc jest kompilowany.

1. Przytrzymaj naciśnięty klawisz CTRL podczas przeciągania zasobów, których chcesz użyć z common.rc do pliku zasobów aplikacji.

Aby użyć innych zasobów obiektów clipart, wykonaj te same czynności. Jedyną różnicą jest to, że otworzysz odpowiedni plik .rc zamiast Common.rc.

> [!NOTE]
> Należy uważać, aby nie przypadkowo przenieść zasoby z Common.rc na stałe. Jeśli klucz CTRL jest przytrzymyny podczas przeciągania zasobów, utworzysz kopię. Jeśli nie przytrzymasz ctrl w dół podczas przeciągania, zasoby zostaną przeniesione. Jeśli obawiasz się, że możesz przypadkowo wszcząć zmiany w pliku Common.rc, kliknij "Nie", gdy pojawi się pytanie, czy zapisać zmiany w Common.rc.

> [!NOTE]
> Pliki zasobów .rc mają specjalny zasób TEXTINCLUDE, który uniemożliwi przypadkowe zapisanie na standardowych plikach .rc.

### <a name="customizing-standard-framework-resources"></a>Dostosowywanie zasobów standardowej struktury

Standardowe zasoby struktury są zwykle uwzględniane w aplikacji przy użyciu polecenia #include w pliku zasobów aplikacji. AppWizard wygeneruje plik zasobów. Ten plik zawiera odpowiednie standardowe zasoby struktury, w zależności od wybranych opcji AppWizard. Można przejrzeć, dodać lub usunąć zasoby, które są uwzględniane przez zmianę dyrektyw w czasie kompilacji. Aby to zrobić, otwórz menu **Zasób** i wybierz polecenie **Ustaw zawiera**. Spójrz na "Dyrektywy kompilacji". Przykład:

```
#include "afxres.rc"
#include "afxprint.rc"
```

Najczęstszym przypadkiem dostosowywania standardowych zasobów struktury jest dodawanie lub usuwanie dodatkowych obejmuje do drukowania, obsługi klienta OLE i serwera OLE.

W niektórych rzadkich przypadkach można dostosować zawartość standardowych zasobów struktury dla danej aplikacji, a nie tylko dodać i usunąć cały plik. Poniższe kroki pokazują, jak można ograniczyć zasoby, które są uwzględnione:

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Aby dostosować zawartość standardowego pliku zasobów

1. Otwórz plik zasobu w języku Visual C++.

1. Za pomocą polecenia Zestaw zasobów `#include` zawiera usuń standardowy plik rc, który chcesz dostosować. Na przykład, aby dostosować pasek narzędzi podglądu `#include "afxprint.rc"` wydruku, usuń wiersz.

1. Otwórz odpowiednie standardowe pliki zasobów w pliku MFC\INCLUDE. Zgodnie z przykładem we wcześniejszej pracy w tym temacie, odpowiedni plik jest MFC\Include\Aafxprint.rc

1. Skopiuj wszystkie zasoby ze standardowego pliku rc do pliku zasobów aplikacji.

1. Zmodyfikuj kopię standardowych zasobów w pliku zasobów aplikacji.

> [!NOTE]
> Nie należy modyfikować zasobów bezpośrednio w standardowych plikach .rc. Spowoduje to zmodyfikowanie zasobów dostępnych w każdej aplikacji, a nie tylko w tej, nad którą obecnie pracujesz.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
