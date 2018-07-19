---
title: Convertstringtobstr — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- ConvertStringToBSTR
dev_langs:
- C++
helpviewer_keywords:
- ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2683daf4fd1293d3fad043037165fa3cbc13de3c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947748"
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR
**Microsoft Specific**  
  
 Konwertuje **char \***  wartość `BSTR`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BSTR __stdcall ConvertStringToBSTR(const char* pSrc)  
```  
  
#### <a name="parameters"></a>Parametry  
 *pSrc*  
 A **char \***  zmiennej.  
  
## <a name="example"></a>Przykład  
  
```cpp 
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
  
**END specyficzny dla Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<comutil.h >  
  
 **Lib:** comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)