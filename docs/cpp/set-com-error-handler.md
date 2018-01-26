---
title: "_set_com_error_handler — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c04c6b2a1177288544536130cf88c8fd8fb673e6
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler
**Microsoft Specific**  
  
 Zastępuje funkcji domyślna, która jest używana do obsługi błędów COM.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stdcall _set_com_error_handler(  
   void (__stdcall *pHandler)(  
      HRESULT hr,   
      IErrorInfo* perrinfo  
   )  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHandler`  
 Wskaźnik do funkcji zamiany.  
  
 `hr`  
 `HRESULT`informacje.  
  
 `perrinfo`  
 `IErrorInfo`obiekt.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie [_com_raise_error —](../cpp/com-raise-error.md) obsługuje wszystkie błędy COM. To zachowanie można zmienić za pomocą `_set_com_error_handler` do wywołania funkcji obsługi błędów.  
  
 Funkcja zastąpienie musi mieć podpisie, który jest równoważna `_com_raise_error`.  
  
## <a name="example"></a>Przykład  
  
```  
// _set_com_error_handler.cpp  
// compile with /EHsc  
#include <stdio.h>  
#include <comdef.h>  
#include <comutil.h>  
  
// Importing ado dll to attempt to establish an ado connection.  
// Not related to _set_com_error_handler   
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")  
  
void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)  
{  
   throw "Unable to establish the connection!";  
}  
  
int main()  
{  
   _set_com_error_handler(_My_com_raise_error);  
   _bstr_t bstrEmpty(L"");  
   _ConnectionPtr Connection = NULL;  
   try  
   {  
      Connection.CreateInstance(__uuidof(Connection));  
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);   
   }  
   catch(char* errorMessage)  
   {  
      printf("Exception raised: %s\n", errorMessage);  
   }  
  
   return 0;  
}  
```  
  
```Output  
Exception raised: Unable to establish the connection!  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<comdef.h >  
  
 **Lib:** Jeśli **wchar_t jest typem natywnym** kompilatora opcja jest włączona, należy użyć comsuppw.lib lub comsuppwd.lib. Jeśli **wchar_t jest typem natywnym** jest wyłączone, należy użyć comsupp.lib. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)