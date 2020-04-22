---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: debad733f351c710ada342e29fa95a4d1ff03b7d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749808"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

Zastępuje domyślną funkcję używaną do obsługi błędów COM. **_set_com_error_handler** jest specyficzne dla firmy Microsoft.

## <a name="syntax"></a>Składnia

```cpp
void __stdcall _set_com_error_handler(
   void (__stdcall *pHandler)(
      HRESULT hr,
      IErrorInfo* perrinfo
   )
);
```

#### <a name="parameters"></a>Parametry

*pHandler (pHandler)*<br/>
Wskaźnik do funkcji zastępczej.

*Hr*<br/>
informacje HRESULT.

*perrinfo (perrinfo)*<br/>
`IErrorInfo`Obiektu.

## <a name="remarks"></a>Uwagi

Domyślnie [_com_raise_error](../cpp/com-raise-error.md) obsługuje wszystkie błędy COM. To zachowanie można zmienić za pomocą **_set_com_error_handler** do wywołania własnej funkcji obsługi błędów.

Funkcja zastępcza musi mieć podpis równoważny `_com_raise_error`podpisowi .

## <a name="example"></a>Przykład

```cpp
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

**Nagłówek:** \<comdef.h>

**Lib:** Jeśli określono opcję kompilatora **/Zc:wchar_t** (wartość domyślna), użyj comsuppw.lib lub comsuppwd.lib. Jeśli określono opcję kompilatora **/Zc:wchar_t-,** użyj pliku comsupp.lib. Aby uzyskać więcej informacji, w tym jak ustawić tę opcję w IDE, zobacz [/Zc:wchar_t (wchar_t jest typem macierzystym).](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>Zobacz też

[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)
