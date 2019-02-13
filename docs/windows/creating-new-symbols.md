---
title: 'Instrukcje: Tworzenie symboli (C++)'
ms.date: 11/04/2016
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
ms.openlocfilehash: 49860f2277dbb462c7e1cd8cb59b86a3edbd3cc9
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226335"
---
# <a name="how-to-create-symbols-c"></a>Instrukcje: Tworzenie symboli (C++)

Gdy jesteś Rozpoczynanie nowego projektu, może okazać się wygodne do mapowania nazwy symboli, które należy spełnić przed tworzenia zasobów, do których zostanie przypisany.

**Symboli zasobów** C++, okno dialogowe umożliwia dodawanie nowych symboli zasobów, zmienianie symboli, które są wyświetlane, lub przejdź do lokalizacji w kodzie źródłowym, w której symbol jest używany.

Okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Nazwa**|Wyświetla nazwę symbolu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md).|
|**Wartość**|Wyświetlana jest wartość liczbowa symbolu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md).|
|**W użyciu**|Po wybraniu Określa, czy symbol jest używany przez co najmniej jednego zasobu. Zasób lub zasoby są wymienione w używana przez pole.|
|**Pokaż symbole tylko do odczytu**|Po wybraniu Wyświetla zasoby tylko do odczytu. Domyślnie **Symbol zasobu** okno dialogowe wyświetla tylko zasoby można modyfikować w pliku skryptu zasobu, ale z wybraniu tej opcji można modyfikować zasoby są wyświetlane pogrubioną czcionką i zasoby tylko do odczytu są wyświetlane w postaci zwykłego tekstu.|
|**Używane przez**|Wyświetla zasobami przy użyciu symbolu zaznaczony na liście symboli. Aby przejść do edytora dla danego zasobu, wybierz zasób w **używane przez** pole, a następnie wybierz **Wyświetl użycie**.|
|**Nowy**|Otwiera **nowy Symbol** okno dialogowe, w którym można zdefiniować nazwę i, jeśli to konieczne, wartość dla nowego identyfikatora zasobu symboliczne.|
|**Change**|Otwiera **Zmień Symbol** okno dialogowe, które umożliwia zmianę nazwy lub wartości symbolu. Jeśli symbol jest dla formantu lub zasobów w użyciu, symbolu można zmienić tylko za pomocą odpowiedniego edytora zasobów. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).|
|**Wyświetl użycie**|Zostanie otwarty zasób, który zawiera symbol w edytorze odpowiednich zasobów.|

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="to-create-a-new-symbol"></a>Aby utworzyć nowy symbol

1. W **symboli zasobów** okna dialogowego wybierz **New**.

1. W **nazwa** wpisz nazwę symbolu.

1. Zaakceptuj wartości przypisane symbolu lub wpisz nową wartość w **wartość** pole.

1. Wybierz **OK** Aby dodać nowy symbol do lista symboli.

> [!NOTE]
> Jeśli wpiszesz nazwę symbolu, który już istnieje, pojawia się komunikat z informacją, że symbol o tej nazwie jest już zdefiniowany. Nie można zdefiniować co najmniej dwóch symbole o takiej samej nazwie, ale można zdefiniować różne symboli z taką samą wartość liczbową. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md) i [ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md).

## <a name="to-view-resource-symbols"></a>Aby wyświetlić symboli zasobów

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Wybierz **symboli zasobów** z menu skrótów, aby wyświetlić tabelę symboli zasobów w **symboli zasobów** okno dialogowe.

   > [!NOTE]
   > Aby wyświetlić wstępnie zdefiniowane symbole, zapoznaj się z **Pokaż symbole tylko do odczytu** pole wyboru.

## <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Aby otworzyć edytora zasobów dla podanego symbolu

Podczas przeglądania symboli w **symboli zasobów**, może chcesz, aby uzyskać więcej informacji dotyczących użycia określonego symbolu. **Wyświetl użycie** przycisk umożliwia szybkie uzyskanie tych informacji.

### <a name="to-move-to-the-resource-editor-where-a-symbol-is-being-used"></a>Aby przejść do edytora zasobów, w którym używany jest symbol

1. Wybierz symbol w **nazwa** pole **symboli zasobów** okno dialogowe.

1. W **używane przez** wybierz typ zasobu, który Cię interesuje.

1. Wybierz **Wyświetl użycie** przycisku.

   Te zasoby są wyświetlane w oknie edytora odpowiednie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)<br/>
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)