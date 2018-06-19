---
title: Wybieranie rekordów i operowanie nimi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a4b76d0b4273e5afb32206336b4aabbfe9294eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090081"
---
# <a name="selecting-and-manipulating-records"></a>Wybieranie rekordów i operowanie nimi
Zwykle po wybraniu rekordy ze źródła danych przy użyciu SQL **wybierz** instrukcji, możesz uzyskać zestaw wyników, który jest zestaw rekordów z tabeli lub zapytania. Z klasami baz danych umożliwia obiekty zestawów rekordów wybierz i korzystać z zestawu wyników. To jest obiekt klasy specyficzne dla aplikacji, która pochodzi z klasy [crecordset —](../../mfc/reference/crecordset-class.md). Podczas definiowania klasy zestawu rekordów, określ źródło danych, aby skojarzyć ją z tabeli używanej i kolumn tabeli. Kreator aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) tworzy klasę z połączeniem z określonego źródła danych. Kreatorzy zapisu [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) funkcji członkowskiej klasy `CRecordset` do zwracania nazwy tabeli. Aby uzyskać więcej informacji na temat Korzystanie z kreatorów, aby utworzyć zestaw rekordów klas, zobacz [obsługi bazy danych, Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md) i [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Przy użyciu [crecordset —](../../mfc/reference/crecordset-class.md) obiektów w czasie wykonywania, można wykonywać następujące czynności:  
  
-   Sprawdź, czy pola danych bieżącego rekordu.  
  
-   Filtrować i sortować zestawu rekordów.  
  
-   Dostosuj domyślne SQL **wybierz** instrukcji.  
  
-   Przewijanie rekordów.  
  
-   Dodawanie, aktualizowanie lub usuwanie rekordów (Jeśli źródło danych jak zestaw rekordów są aktualizowalne).  
  
-   Sprawdź, czy zestaw rekordów umożliwia ponowne wysyłanie zapytania, a następnie Odśwież zawartość w zestawie rekordów.  
  
 Po zakończeniu przy użyciu obiektu zestawu rekordów, zamknij i zniszcz go. Aby uzyskać więcej informacji na temat zestawów rekordów, zobacz [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [ODBC i MFC](../../data/odbc/odbc-and-mfc.md)