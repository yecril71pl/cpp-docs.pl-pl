---
title: Wymiana pól (RFX) rekordów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03b827b9f6ec1b1a378b1ffd04aa2c1e1c6aa111
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087763"
---
# <a name="record-field-exchange-rfx"></a>Wymiana pól rekordów (RFX)

Klasy baz danych MFC ODBC zautomatyzować przenoszenie danych między źródłem danych i [rekordów](../../data/odbc/recordset-odbc.md) obiektu. Po utworzeniu klasy pochodnej klasy z [CRecordset](../../mfc/reference/crecordset-class.md) i nie używaj zbiorcze pobieranie z wiersza, dane są przesyłane przez mechanizm pól rekordów (RFX) programu exchange.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza w pochodnej `CRecordset` klasy, struktura używa mechanizmu programu exchange (zbiorcze RFX) pole rekordu zbiorczego transferu danych. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
RFX przypomina wymiana danych okna dialogowego (DDX). Przenoszenie danych między źródłem danych i elementy członkowskie danych pola zestawu rekordów wymaga wielu wywołań do zestawu rekordów [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcji i dużą interakcji między platformę i [ODBC](../../data/odbc/odbc-basics.md). Mechanizm RFX jest bezpieczny i powoduje zapisanie pracy, takich jak wywoływanie funkcji ODBC `::SQLBindCol`. Aby uzyskać więcej informacji na temat DDX zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md).  
  
RFX przede wszystkim jest przezroczysty dla użytkownika. Jeśli zadeklarujesz Twoich zajęciach rekordów za pomocą Kreatora aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX ma wbudowaną je automatycznie. Klasa zestaw rekordów musi pochodzić z klasy bazowej `CRecordset` dostarczone przez platformę. Kreator aplikacji MFC pozwala utworzyć klasę początkowego zestawu rekordów. **Dodaj klasę** pozwala dodać inne klasy zestawu rekordów, gdy ich potrzebujesz. Aby uzyskać więcej informacji i przykładów, zobacz [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
Należy ręcznie dodać niewielką ilość kodu RFX w trzech przypadkach, gdy chcesz:  
  
- Użyć sparametryzowanych zapytań. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
- Wykonanie sprzężeń zewnętrznych (przy użyciu jednego zestawu rekordów kolumn z co najmniej dwóch tabel). Aby uzyskać więcej informacji, zobacz [zestaw rekordów: wykonywanie Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
- Dynamiczne powiązanie kolumn danych. Jest to rzadziej niż parametryzacji. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
Aby uzyskać większą wiedzę RFX zobacz [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
W poniższych tematach opisano szczegóły przy użyciu obiektów zestaw rekordów:  
  
- [Wymiana pól rekordów: używanie RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
- [Wymiana pól rekordów: używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
- [Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## <a name="see-also"></a>Zobacz też  

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Obsługa bazy danych, kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)