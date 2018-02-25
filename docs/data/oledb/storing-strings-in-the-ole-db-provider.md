---
title: "Przechowywanie ciągów w dostawcy OLE DB | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 018bf17cbd4106b4b76ec58ab524d8da6f14b62d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Przechowywanie ciągów w dostawcy OLE DB
W MyProviderRS.h, OLE DB Provider Kreator ATL tworzy domyślny rekord użytkownika o nazwie `CWindowsFile`. Aby obsługiwać dwa ciągi, zmodyfikuj `CWindowsFile` lub Dodaj rekord użytkownika, jak pokazano w poniższym kodzie:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
class CAgentMan:   
   public WIN32_FIND_DATA  
   DWORD dwBookmark;              // Add this  
   TCHAR szCommand[256];          // Add this  
   TCHAR szText[256];             // Add this  
   TCHAR szCommand2[256];         // Add this  
   TCHAR szText2[256];            // Add this  
  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP()  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText)   
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)  
END_PROVIDER_COLUMN_MAP()  
   bool operator==(const CAgentMan& am) // This is optional   
   {  
      return (lstrcmpi(cFileName, wf.cFileName) == 0);  
   }  
};  
```  
  
 Elementy członkowskie danych `szCommand` i `szText` reprezentują dwa ciągi z `szCommand2` i `szText2` zapewnienie dodatkowych kolumn, w razie potrzeby. Element członkowski danych `dwBookmark` nie jest wymagane dla tego prostego dostawcy tylko do odczytu, ale później służy do dodawania `IRowsetLocate` interfejsu; zobacz [udoskonalanie prostego odczytu tylko dostawcy](../../data/oledb/enhancing-the-simple-read-only-provider.md). `==` Operator porównuje wystąpienia (Implementowanie Ten operator jest opcjonalny).  
  
 Po zakończeniu dostawcy należy skompilować i uruchomić. Aby przetestować dostawcę, należy konsumentów ze zgodnymi funkcji. [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md) przedstawiono sposób tworzenia użytkownika testu. Uruchomić klienta testowego z dostawcą. Sprawdź, czy konsumenta test pobiera odpowiednie ciągi od dostawcy, po kliknięciu **Uruchom** przycisk **Test konsumenta** okno dialogowe.  
  
 Dostawca pomyślnie zostały przetestowane, można zwiększyć jego funkcjonalność implementując dodatkowe interfejsy. Przykład znajduje się w [udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md)