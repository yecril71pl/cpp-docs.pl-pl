---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 226dce24de68edd66ca68c43e41ce0cb5b8a1b48
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857297"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

Zastępuje domyślną funkcję, która jest używana do obsługi błędów COM. **_set_com_error_handler** to specyficzny dla firmy Microsoft.

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

*pHandler*<br/>
Wskaźnik do funkcji zastępczej.

*wysoki*<br/>
Informacje o HRESULT.

*perrinfo*<br/>
`IErrorInfo` obiektu.

## <a name="remarks"></a>Uwagi

Domyślnie [_com_raise_error](../cpp/com-raise-error.md) obsługuje wszystkie błędy com. Można zmienić to zachowanie przy użyciu **_set_com_error_handler** do wywołania własnej funkcji obsługi błędów.

Funkcja zastępująca musi mieć sygnaturę odpowiadającą wartości `_com_raise_error`.

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

**Nagłówek:** \<comdef. h >

**Lib:** Jeśli określono opcję kompilatora **/Zc: wchar_t** (wartość domyślna), użyj comsuppw. lib lub comsuppwd. lib. Jeśli jest określona opcja **/Zc: wchar_t-** Compiler, użyj comsupp. lib. Aby uzyskać więcej informacji, w tym o sposobie ustawiania tej opcji w IDE, zobacz [/Zc: wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Zobacz także

[Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)
