---
title: ConvertBSTRToString
ms.date: 11/04/2016
f1_keywords:
- ConvertBSTRToString
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
ms.openlocfilehash: 1d0ad8727dd4d5ec06a45ec26c67dd3ad268f524
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189528"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Specyficzne dla firmy Microsoft**

Konwertuje wartość `BSTR` na `char *`.

## <a name="syntax"></a>Składnia

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>Parametry

*pSrc*<br/>
Zmienna BSTR.

## <a name="remarks"></a>Uwagi

**ConvertBSTRToString** przypisuje ciąg, który należy usunąć.

## <a name="example"></a>Przykład

```cpp
// ConvertBSTRToString.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")

int main() {
   BSTR bstrText = ::SysAllocString(L"Test");
   wprintf_s(L"BSTR text: %s\n", bstrText);

   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);
   printf_s("char * text: %s\n", lpszText2);

   SysFreeString(bstrText);
   delete[] lpszText2;
}
```

```Output
BSTR text: Test
char * text: Test
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<comutil. h >

**Lib:** comsuppw. lib lub comsuppwd. lib (patrz [/Zc: Wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)
