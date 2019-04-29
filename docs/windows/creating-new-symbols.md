---
title: 'Instrukcje: Tworzenie symboli (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 8bb73c1a9e8d253492a7068c444dd7ddea8417da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350952"
---
# <a name="how-to-create-symbols-c"></a>Instrukcje: Tworzenie symboli (C++)

Gdy jesteś Rozpoczynanie nowego projektu, może okazać się wygodne do mapowania nazwy symboli, które należy spełnić przed tworzenia zasobów, do których zostanie przypisany.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [jak: Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md).

**Symboli zasobów** okno dialogowe umożliwia dodawanie nowych symboli zasobów, zmienianie symboli, które są wyświetlane, lub przejdź do lokalizacji w kodzie źródłowym, w której symbol jest używany.

Okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|--------------------------|------------------------------------------|
|**Nazwa**|Wyświetla nazwę symbolu.<br/><br/>Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md).|
|**Wartość**|Wyświetlana jest wartość liczbowa symbolu.<br/><br/>Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md).|
|**W użyciu**|Po wybraniu Określa, czy symbol jest używany przez co najmniej jednego zasobu.<br/><br/>Zasób lub zasoby są wymienione w **posługują się** pole.|
|**Pokaż symbole tylko do odczytu**|Po wybraniu Wyświetla zasoby tylko do odczytu.<br/><br/>Domyślnie **Symbol zasobu** okno dialogowe wyświetla tylko zasoby można modyfikować w pliku skryptu zasobu, ale z wybraniu tej opcji można modyfikować zasoby są wyświetlane pogrubioną czcionką i zasoby tylko do odczytu są wyświetlane w postaci zwykłego tekstu.|
|**Używane przez**|Wyświetla zasobami przy użyciu symbolu zaznaczony na liście symboli.<br/><br/>Aby przejść do edytora dla danego zasobu, wybierz zasób w **posługują się** pole, a następnie wybierz **Wyświetl użycie**.|
|**Nowy**|Otwiera **nowy Symbol** okno dialogowe, które pozwala zdefiniować nazwę i, jeśli to konieczne, wartość dla nowego identyfikatora zasobu symboliczne.|
|**Change**|Otwiera **Zmień Symbol** okno dialogowe, które umożliwia zmianę nazwy lub wartości symbolu.<br/><br/>Jeśli symbol jest dla formantu lub zasobów w użyciu, symbolu można zmienić tylko za pomocą odpowiedniego edytora zasobów. Aby uzyskać więcej informacji, zobacz [Zarządzanie symbole](../windows/changing-unassigned-symbols.md).|
|**Wyświetl użycie**|Zostanie otwarty zasób, który zawiera symbol w edytorze odpowiednich zasobów.|

## <a name="create-symbols"></a>Tworzenie symboli

### <a name="to-create-a-new-symbol"></a>Aby utworzyć nowy symbol

1. W **symboli zasobów** okna dialogowego wybierz **New**.

1. W **nazwa** wpisz nazwę symbolu.

1. Zaakceptuj wartości przypisane symbolu lub wpisz nową wartość w **wartość** pole.

1. Wybierz **OK** Aby dodać nowy symbol do lista symboli.

> [!NOTE]
> Jeśli wpiszesz nazwę symbolu, który już istnieje, pojawia się komunikat z informacją, że symbol o tej nazwie jest już zdefiniowany. Nie można zdefiniować co najmniej dwóch symbole o takiej samej nazwie, ale można zdefiniować różne symboli z taką samą wartość liczbową.

## <a name="to-view-resource-symbols"></a>Aby wyświetlić symboli zasobów

W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), kliknij prawym przyciskiem myszy użytkownika *.rc* plik i wybierz **symboli zasobów** do wyświetlenia w tabeli symboli zasobów **symboli zasobów**okno dialogowe.

> [!NOTE]
> Aby wyświetlić wstępnie zdefiniowane symbole, zapoznaj się z **Pokaż symbole tylko do odczytu** pole wyboru.

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Aby otworzyć edytora zasobów dla podanego symbolu

Podczas przeglądania symboli w **symboli zasobów**, może chcesz, aby uzyskać więcej informacji dotyczących użycia określonego symbolu. **Wyświetl użycie** przycisk umożliwia szybkie uzyskanie tych informacji.

1. W **symboli zasobów** okno dialogowe w **nazwa** wybierz symbol.

1. W **używane przez** wybierz typ zasobu, który Cię interesuje.

1. Wybierz **Wyświetl użycie** przycisku.

   Te zasoby są wyświetlane w oknie edytora odpowiednie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>
[Instrukcje: Zarządzanie symbolami](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)<br/>