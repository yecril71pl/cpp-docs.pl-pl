---
title: "Convertstringtobstr — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ConvertStringToBSTR
dev_langs: C++
helpviewer_keywords: ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2e6e62a4de1e1bc4e38bc05fa1012867c2e7fc3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR
**Dotyczące firmy Microsoft**  
  
 Konwertuje **char \***  do wartości `BSTR`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      BSTR __stdcall ConvertStringToBSTR(  
   const char* pSrc  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSrc`  
 A **char \***  zmiennej.  
  
## <a name="example"></a>Przykład  
  
```  
// ConvertStringToBSTR.cpp  
#include <comutil.h>  
#include <stdio.h>  
  
#pragma comment(lib, "comsuppw.lib")  
#pragma comment(lib, "kernel32.lib")  
  
int main() {  
   char* lpszText = "Test";  
   printf_s("char * text: %s\n", lpszText);  
  
   BSTR bstrText = _com_util::ConvertStringToBSTR(lpszText);  
   wprintf_s(L"BSTR text: %s\n", bstrText);  
  
   SysFreeString(bstrText);  
}  
```  
  
```Output  
char * text: Test  
BSTR text: Test  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** comutil.h  
  
 **Lib:** comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)