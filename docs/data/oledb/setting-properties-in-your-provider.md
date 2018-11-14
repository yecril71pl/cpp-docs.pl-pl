---
title: Ustawianie właściwości w dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 149e6f37de64a1133258f5bbc550896a4fb22a9f
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556663"
---
# <a name="setting-properties-in-your-provider"></a>Ustawianie właściwości w dostawcy

Znajdź grupy właściwości i Identyfikatora właściwości dla właściwości, które chcesz. Aby uzyskać więcej informacji, zobacz [właściwości OLE DB](https://docs.microsoft.com/previous-versions/windows/desktop/ms722734(v=vs.85)) w **OLE DB Podręcznik programisty**.

W kodzie dostawcy generowane przez kreatora należy znaleźć map właściwości odpowiadającego grupie właściwości. Nazwa grupy właściwości zazwyczaj odnosi się do nazwy obiektu. Właściwości polecenia i zestawu wierszy można znaleźć w polecenia lub zestaw wierszy; właściwości źródła i Inicjowanie danych można znaleźć w obiektu źródła danych.

Mapy właściwości, należy dodać [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) makra. PROPERTY_INFO_ENTRY_EX przyjmuje cztery parametry:

- Identyfikator właściwości odpowiadający Twojej właściwości. Usuń najpierw siedem znaków ("DBPROP_") z przodu nazwy właściwości. Na przykład, jeśli chcesz dodać `DBPROP_MAXROWS`, przekazać `MAXROWS` jako pierwszy element. Jeśli jest to właściwość niestandardowa, należy przekazać Pełna nazwa identyfikatora GUID (na przykład `DBMYPROP_MYPROPERTY`).

- Typ wariantu właściwości (w [właściwości OLE DB](https://docs.microsoft.com/previous-versions/windows/desktop/ms722734(v=vs.85)) w **OLE DB Podręcznik programisty**). Wprowadź VT_ odpowiadającego typowi (lub VT_I2 VT_BOOL.) na typ danych.

- Flagi, aby wskazać, czy właściwość jest czytelny i zapisywalny i grupy, do której należy. Na przykład poniższy kod wskazuje właściwości odczytu/zapisu, należącego do grupy wierszy:

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- Podstawowa wartość właściwości. Może to być `VARIANT_FALSE` dla logicznego wpisz lub zero dla typu integer, na przykład. Właściwość ma tę wartość, chyba że zostanie on zmieniony.

    > [!NOTE]
    > Niektóre właściwości są połączone lub łączyć je do innych właściwości, takie jak zakładek lub aktualizacji. Po użytkownik ustawia jedną właściwość na wartość true, mogą również ustawić inną właściwość. Szablony dostawców OLE DB obsługuje to za pomocą metody [CUtlProps::OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Właściwości ignorowane przez dostawców OLE DB firmy Microsoft

Dostawcy OLE DB firmy Microsoft Ignoruj następujące właściwości OLE DB:

- `DBPROP_MAXROWS` działa tylko w przypadku dostawcy tylko do odczytu (czyli, gdzie `DBPROP_IRowsetChange` i `DBPROP_IRowsetUpdate` są **false**); w przeciwnym razie ta właściwość nie jest obsługiwana.

- `DBPROP_MAXPENDINGROWS` jest ignorowana. Dostawca określa swój własny limit.

- `DBPROP_MAXOPENROWS` jest ignorowana. Dostawca określa swój własny limit.

- `DBPROP_CANHOLDROWS` jest ignorowana. Dostawca określa swój własny limit.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)