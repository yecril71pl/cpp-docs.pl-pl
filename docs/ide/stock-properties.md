---
title: Podstawowy właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- stock properties, about stock properties
- stock properties
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 201e6f0591d446dc0e6b036cfd7ac6f3028eb812
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430270"
---
# <a name="stock-properties"></a>Właściwości podstawowe

Jeśli chcesz dodać właściwość do dispinterface MFC przy użyciu [Kreator dodawania właściwości](../ide/idl-attributes-add-property-wizard.md), można wybrać właściwości podstawowych z **nazwa właściwości** listy w [nazwy](../ide/names-add-property-wizard.md) strony Kreator. Właściwości są następujące:

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|**Wygląd**|Zwraca lub ustawia wartość określającą, wygląd formantu. Kontrolki **wygląd** właściwości można uwzględnić lub pominąć efekty trójwymiarowych. Jest to właściwość otoczenia odczytu/zapisu.|
|`BackColor`|Zwraca lub ustawia formantu otoczenia `BackColor` właściwość kolor z palety (RGB) lub kolor wstępnie zdefiniowanego. Domyślnie jej wartość odpowiada kolor pierwszego planu kontener formantu. Jest to właściwość otoczenia odczytu/zapisu.|
|`BorderStyle`|Zwraca lub ustawia styl obramowania kontrolki. Jest to właściwość odczytu/zapisu.|
|**Podpis**|Zwraca lub ustawia formantu **podpis** właściwości. Podpis jest tytuł okna. **Podpis** nie ma przypisanego **zmiennej składowej** typ implementacji.|
|**Włączone**|Zwraca lub ustawia formantu **włączone** właściwości. Kontrolka w postaci włączone może odpowiadać na zdarzenia generowane przez użytkownika.|
|**Czcionka**|Zwraca lub ustawia czcionkę otoczenia formantu. Wartość null, jeśli kontrolka ma nie czcionki.|
|`ForeColor`|Zwraca lub ustawia formantu otoczenia `ForeColor` właściwości.|
|**hWnd**|Zwraca lub ustawia formantu **hWnd** właściwości. **hWnd** nie ma przypisanego **zmiennej składowej** typ implementacji.|
|**ReadyState**|Zwraca lub ustawia formantu **ReadyState** właściwości. Formant może być niezainicjowanej, zainicjowane, ładowanie, interakcyjnego lub pełne. Zobacz [READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx) w *Internet SDK* Aby uzyskać więcej informacji.|
|**Tekst**|Zwraca lub ustawia tekst zawarty w kontrolce. **Tekst** nie ma przypisanego **zmiennej składowej** typ implementacji.|

## <a name="see-also"></a>Zobacz też

[Dodawanie właściwości](../ide/adding-a-property-visual-cpp.md)<br>
[Atrybuty IDL, Kreator dodawania właściwości](../ide/idl-attributes-add-property-wizard.md)