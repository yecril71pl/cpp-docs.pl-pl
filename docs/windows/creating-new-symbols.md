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
ms.openlocfilehash: 7dda3dc04b055226a0ae9788e6a98f6261256e7f
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954890"
---
# <a name="how-to-create-symbols-c"></a>Instrukcje: Tworzenie symboli (C++)

Gdy jesteś Rozpoczynanie nowego projektu, może okazać się wygodne do mapowania nazwy symboli, które należy spełnić przed tworzenia zasobów, do których zostanie przypisany.

**Symboli zasobów** okno dialogowe umożliwia dodawanie nowych symboli zasobów, zmienianie symboli, które są wyświetlane, lub przejdź do lokalizacji w kodzie źródłowym, w której symbol jest używany.

Okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|--------------------------|------------------------------------------|
|**Nazwa**|Wyświetla nazwę symbolu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md).|
|**Wartość**|Wyświetlana jest wartość liczbowa symbolu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md).|
|**W użyciu**|Po wybraniu Określa, czy symbol jest używany przez co najmniej jednego zasobu. Zasób lub zasoby są wymienione w używana przez pole.|
|**Pokaż symbole tylko do odczytu**|Po wybraniu Wyświetla zasoby tylko do odczytu. Domyślnie **Symbol zasobu** okno dialogowe wyświetla tylko zasoby można modyfikować w pliku skryptu zasobu, ale z wybraniu tej opcji można modyfikować zasoby są wyświetlane pogrubioną czcionką i zasoby tylko do odczytu są wyświetlane w postaci zwykłego tekstu.|
|**Używane przez**|Wyświetla zasobami przy użyciu symbolu zaznaczony na liście symboli. Aby przejść do edytora dla danego zasobu, wybierz zasób w **używane przez** pole, a następnie wybierz **Wyświetl użycie**.|
|**Nowy**|Otwiera **nowy Symbol** okno dialogowe, w którym można zdefiniować nazwę i, jeśli to konieczne, wartość dla nowego identyfikatora zasobu symboliczne.|
|**Change**|Otwiera **Zmień Symbol** okno dialogowe, które umożliwia zmianę nazwy lub wartości symbolu. Jeśli symbol jest dla formantu lub zasobów w użyciu, symbolu można zmienić tylko za pomocą odpowiedniego edytora zasobów. Aby uzyskać więcej informacji, zobacz [Zarządzanie symbole](../windows/changing-unassigned-symbols.md).|
|**Wyświetl użycie**|Zostanie otwarty zasób, który zawiera symbol w edytorze odpowiednich zasobów.|

## <a name="create-symbols"></a>Tworzenie symboli

Aby utworzyć nowy symbol:

1. W **symboli zasobów** okna dialogowego wybierz **New**.

1. W **nazwa** wpisz nazwę symbolu.

1. Zaakceptuj wartości przypisane symbolu lub wpisz nową wartość w **wartość** pole.

1. Wybierz **OK** Aby dodać nowy symbol do lista symboli.

> [!NOTE]
> Jeśli wpiszesz nazwę symbolu, który już istnieje, pojawia się komunikat z informacją, że symbol o tej nazwie jest już zdefiniowany. Nie można zdefiniować co najmniej dwóch symbole o takiej samej nazwie, ale można zdefiniować różne symboli z taką samą wartość liczbową.

Aby wyświetlić symboli zasobów:

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [jak: Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Wybierz **symboli zasobów** z menu skrótów, aby wyświetlić tabelę symboli zasobów w **symboli zasobów** okno dialogowe.

   > [!NOTE]
   > Aby wyświetlić wstępnie zdefiniowane symbole, zapoznaj się z **Pokaż symbole tylko do odczytu** pole wyboru.

Aby otworzyć edytora zasobów dla podanego symbolu:

Podczas przeglądania symboli w **symboli zasobów**, może chcesz, aby uzyskać więcej informacji dotyczących użycia określonego symbolu. **Wyświetl użycie** przycisk umożliwia szybkie uzyskanie tych informacji.

1. Wybierz symbol w **nazwa** pole **symboli zasobów** okno dialogowe.

1. W **używane przez** wybierz typ zasobu, który Cię interesuje.

1. Wybierz **Wyświetl użycie** przycisku.

   Te zasoby są wyświetlane w oknie edytora odpowiednie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>
[Instrukcje: Zarządzanie symbolami](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)<br/>