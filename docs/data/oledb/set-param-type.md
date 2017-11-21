---
title: SET_PARAM_TYPE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SET_PARAM_TYPE
dev_langs: C++
helpviewer_keywords: SET_PARAM_TYPE macro
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b8fb0ab344f5ee9e34c1157d661bced369afac41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setparamtype"></a>SET_PARAM_TYPE
Określa `COLUMN_ENTRY` makra, które należy wykonać `SET_PARAM_TYPE` makro danych wejściowych, wyjściowych lub wejścia/wyjścia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
SET_PARAM_TYPE(  
type  
 )  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 [in] Typ dla parametru.  
  
## <a name="remarks"></a>Uwagi  
 Dostawcy obsługują tylko typy wejścia/wyjścia parametrów, które są obsługiwane w źródle danych. Typ jest kombinacją co najmniej jeden **DBPARAMIO** wartości (zobacz [struktury DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) w *OLE DB Podręcznik programisty*):  
  
-   **DBPARAMIO_NOTPARAM** metodzie dostępu nie ma parametrów. Zwykle ustawić **eParamIO** tej wartości w metodach dostępu wiersza przypomnieć użytkownikowi, że parametry są ignorowane.  
  
-   **DBPARAMIO_INPUT** parametru wejściowego.  
  
-   **DBPARAMIO_OUTPUT** parametru wyjściowego.  
  
-   **DBPARAMIO_INPUT &#124; DBPARAMIO_OUTPUT** parametr jest wartością wejściową i parametru wyjściowego.  
  
## <a name="example"></a>Przykład  
```cpp  
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
``` 
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)