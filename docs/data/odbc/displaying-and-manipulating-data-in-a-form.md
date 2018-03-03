---
title: "Wyświetlanie i manipulowanie danymi w formularzu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1a7960780f1f83833e25c9a094a36314a299a042
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Wyświetlanie danych w formularzu i operowanie nimi
Wiele aplikacji dostęp do danych wybierz dane i wyświetl ją w polach w formularzu. Klasy bazy danych [CRecordView](../../mfc/reference/crecordview-class.md) daje [CFormView](../../mfc/reference/cformview-class.md) obiektu podłączone bezpośrednio do obiektu zestawu rekordów. Używa widoku rekordu [wymiana danych okna dialogowego (DDX)](../../mfc/dialog-data-exchange-and-validation.md) Przenieś wartości pól bieżącego rekordu w zestawie do formantów w formularzu i przenieść zaktualizowane informacje z powrotem do zestawu rekordów. Zestaw rekordów, z kolei używa wymiana pól rekordów (RFX) aby przenoszenie danych między jego elementy członkowskie danych pola i odpowiednie kolumny w tabeli w źródle danych.  
  
 Można użyć Kreatora aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) można utworzyć klasy widok, a jego klasa skojarzonych rekordów w połączeniu.  
  
 Widoku rekordu i jego rekordów zostaną zniszczone po zamknięciu dokumentu. Aby uzyskać więcej informacji na temat widoków rekordów, zobacz [widoków rekordów](../../data/record-views-mfc-data-access.md). Aby uzyskać więcej informacji na temat RFX, zobacz [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Zobacz też  
 [ODBC i MFC](../../data/odbc/odbc-and-mfc.md)