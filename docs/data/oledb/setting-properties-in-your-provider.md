---
title: Ustawianie właściwości w dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 905a9bb32544dbd7453d46362e100047516d22a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209576"
---
# <a name="setting-properties-in-your-provider"></a>Ustawianie właściwości w dostawcy

Znajdź grupę właściwości i identyfikator właściwości dla właściwości, którą chcesz. Aby uzyskać więcej informacji, zobacz [OLE DB właściwości](/previous-versions/windows/desktop/ms722734(v=vs.85)) w **kompendium programisty OLE DB**.

W kodzie dostawcy wygenerowanym przez Kreatora Znajdź mapę właściwości odpowiadającą grupie właściwości. Nazwa grupy właściwości zazwyczaj odpowiada nazwie obiektu. Właściwości polecenia i zestawu wierszy można znaleźć w poleceniu lub zestawie wierszy. właściwości źródła danych i inicjowania można znaleźć w obiekcie źródła danych.

Na mapie właściwości Dodaj makro [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) . PROPERTY_INFO_ENTRY_EX przyjmuje cztery parametry:

- Identyfikator właściwości odpowiadający właściwości. Usuń pierwsze siedem znaków ("DBPROP_") od początku nazwy właściwości. Na przykład, jeśli chcesz dodać `DBPROP_MAXROWS`, Przekaż `MAXROWS` jako pierwszy element. Jeśli jest to właściwość niestandardowa, Przekaż pełną nazwę identyfikatora GUID (na przykład `DBMYPROP_MYPROPERTY`).

- Typ Variant właściwości (WE [właściwościach OLE DB](/previous-versions/windows/desktop/ms722734(v=vs.85)) w **odniesieniu do OLE DB programisty**). Wprowadź typ VT_ (na przykład VT_BOOL lub VT_I2) odpowiadający typowi danych.

- Flagi wskazujące, czy właściwość jest czytelna i zapisywalna oraz do grupy, do której należy. Na przykład poniższy kod wskazuje właściwość odczytu/zapisu należącej do grupy zestawów wierszy:

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- Wartość podstawowa właściwości. Może to być `VARIANT_FALSE` dla typu Boolean lub zero dla typu Integer, na przykład. Właściwość ma tę wartość, o ile nie została zmieniona.

    > [!NOTE]
    > Niektóre właściwości są połączone lub są powiązane z innymi właściwościami, takimi jak zakładki lub aktualizacje. Gdy konsument ustawi jedną właściwość na true, można również ustawić inną właściwość. Szablony dostawcy OLE DB obsługują tę procedurę za pomocą metody [CUtlProps:: OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Właściwości ignorowane przez dostawców OLE DB firmy Microsoft

Dostawcy OLE DB firmy Microsoft ignorują następujące właściwości OLE DB:

- `DBPROP_MAXROWS` działa tylko w przypadku dostawców tylko do odczytu (czyli, w których `DBPROP_IRowsetChange` i `DBPROP_IRowsetUpdate` są **fałszywe**); w przeciwnym razie ta właściwość nie jest obsługiwana.

- `DBPROP_MAXPENDINGROWS` jest ignorowana; Dostawca określa swój własny limit.

- `DBPROP_MAXOPENROWS` jest ignorowana; Dostawca określa swój własny limit.

- `DBPROP_CANHOLDROWS` jest ignorowana; Dostawca określa swój własny limit.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
