---
title: "Klasy wyjątków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.exception
dev_langs: C++
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b848cf1a839940925222a50ce016ba91da4d371d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exception-classes"></a>Klasy wyjątków
Biblioteka klas udostępnia mechanizm obsługi wyjątków, na podstawie klasy `CException`. Struktura aplikacji używa wyjątków w jego kod; można także używać ich w należy do Ciebie. Aby uzyskać więcej informacji, zobacz artykuł [wyjątki](../mfc/exception-handling-in-mfc.md). Mogą pochodzić własnych typów wyjątków z `CException`.  
  
 MFC zawiera klasę wyjątku, z którego mogą pochodzić własne wyjątek, a także klasy wyjątków dla wszystkich wyjątków, który go obsługuje.  
  
 [Cexception —](../mfc/reference/cexception-class.md)  
 Klasa podstawowa dla wyjątków.  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Wystąpił wyjątek archiwum.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Wystąpił wyjątek awarii w operacji bazy danych DAO.  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 Wystąpił wyjątek awarii podczas przetwarzania bazy danych ODBC.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Wyjątek zorientowane na plik.  
  
 [CMemoryException](../mfc/reference/cmemoryexception-class.md)  
 Wystąpił wyjątek braku pamięci.  
  
 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)  
 Wystąpił wyjątek wynikające z używa nieobsługiwanej funkcji.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Wystąpił wyjątek awarii podczas przetwarzania OLE. Ta klasa jest używana zarówno kontenery i serwery.  
  
 [COleDispatchException](../mfc/reference/coledispatchexception-class.md)  
 Wystąpił wyjątek wynikającego z wystąpił błąd podczas automatyzacji. Automatyzacja wyjątki są zgłaszane przez serwery automatyzacji i przechwycony przez klientów automatyzacji.  
  
 [CResourceException](../mfc/reference/cresourceexception-class.md)  
 Wystąpił wyjątek awarii można załadować zasobu systemu Windows.  
  
 [CUserException](../mfc/reference/cuserexception-class.md)  
 Wyjątek, można zatrzymać operację zainicjowane przez użytkownika. Zazwyczaj użytkownik został powiadomiony o problemie przed tym wyjątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

