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
ms.openlocfilehash: a3586fb33c30148c870b096d0d49a41d7ad8c6c8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33335445"
---
# <a name="stock-properties"></a>Właściwości podstawowe
Jeśli dodajesz właściwość dispinterface MFC przy użyciu [Dodaj Kreatora właściwości](../ide/idl-attributes-add-property-wizard.md), można wybrać właściwości standardowych z **nazwa właściwości** na liście [nazwy](../ide/names-add-property-wizard.md) strony Kreator. Właściwości są następujące:  
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|**Wygląd**|Zwraca lub ustawia wartość, która określa wygląd formantu. Kontrolki **wygląd** właściwości można uwzględnić lub pominąć efekty trójwymiarowych. To jest właściwością otoczenia odczytu/zapisu.|  
|`BackColor`|Zwraca lub konfiguruje formantu otoczenia `BackColor` właściwości kolorów palety (RGB) lub kolor wstępnie zdefiniowanego systemu. Domyślnie wartość odpowiada kolor pierwszego planu formantu kontenera. To jest właściwością otoczenia odczytu/zapisu.|  
|`BorderStyle`|Zwraca lub ustawia styl obramowania formantu. Jest to właściwość odczytu/zapisu.|  
|**Podpis**|Zwraca lub konfiguruje formantu **podpis** właściwości. Podpis jest tytuł okna. **Podpis** nie ma **zmiennej członkowskiej** typ implementacji.|  
|**włączone**|Zwraca lub konfiguruje formantu **włączone** właściwości. Formant włączone może odpowiadać na zdarzenia generowane przez użytkownika.|  
|**Czcionki**|Zwraca lub ustawia czcionkę otoczenia formantu. Wartość null, jeśli formant nie ma żadnych czcionki.|  
|`ForeColor`|Zwraca lub konfiguruje formantu otoczenia `ForeColor` właściwości.|  
|**Właściwość hWnd**|Zwraca lub konfiguruje formantu **hWnd** właściwości. **Właściwość hWnd** nie ma **zmiennej członkowskiej** typ implementacji.|  
|**ReadyState**|Zwraca lub konfiguruje formantu **ReadyState** właściwości. Formant może być niezainicjowanej, zainicjowane, ładowania, interakcyjnego lub pełną. Zobacz [READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx) w *Internet SDK* Aby uzyskać więcej informacji.|  
|**Tekst**|Zwraca lub ustawia tekst wyświetlany w formancie. **Tekst** nie ma **zmiennej członkowskiej** typ implementacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie właściwości](../ide/adding-a-property-visual-cpp.md)   
 [Atrybuty IDL, Kreator dodawania właściwości](../ide/idl-attributes-add-property-wizard.md)