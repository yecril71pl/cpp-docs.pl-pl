---
title: Przechowywanie ciągów w dostawcy OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84ee07f236ac7ec79149b1cb36f358598f9c6c12
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112697"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Przechowywanie ciągów w dostawcy OLE DB

W MyProviderRS.h, ATL OLE DB Provider Kreator tworzy rekord użytkownika domyślnego o nazwie `CWindowsFile`. Aby obsługiwać dwa ciągi, zmodyfikuj `CWindowsFile` lub dodać rekord użytkownika, jak pokazano w poniższym kodzie:  
  
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
  
Elementy członkowskie danych `szCommand` i `szText` reprezentują dwa ciągi przy użyciu `szCommand2` i `szText2` zapewnienie dodatkowych kolumn, jeśli to konieczne. Element członkowski danych `dwBookmark` nie jest wymagany dla tego prostego dostawcy tylko do odczytu, ale jest używany później dodać `IRowsetLocate` interfejsu; zobacz [udoskonalanie prostego odczytu tylko dostawcy](../../data/oledb/enhancing-the-simple-read-only-provider.md). `==` Operator porównuje wystąpienia (Implementowanie Ten operator jest opcjonalny).  
  
Gdy jest to wykonywane, dostawca powinien być gotowe do kompilowania i uruchamiania. Aby przetestować dostawcę, należy odbiorców za pomocą funkcji dopasowywania. [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md) pokazuje, jak utworzyć odbiorcę testu. Uruchom klienta testowego z dostawcą. Sprawdź, czy odbiorcy test pobiera odpowiednie ciągi od dostawcy, po kliknięciu **Uruchom** znajdujący się w **Test konsumenta** okno dialogowe.  
  
Twój dostawca zostały pomyślnie przetestowane, można zwiększyć jego działanie, implementując dodatkowe interfejsy. Przykład został przedstawiony na [udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
## <a name="see-also"></a>Zobacz też  

[Implementowanie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md)