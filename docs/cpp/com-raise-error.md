---
title: _com_raise_error — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f38a0d97b90f1512e5f16b3bd147bda3e0614e4f
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947855"
---
# <a name="comraiseerror"></a>_com_raise_error
**Microsoft Specific**  
  
 Zgłasza [_com_error](../cpp/com-error-class.md) w odpowiedzi na błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *godz.*  
 Informacje o HRESULT.  
  
 *perrinfo*  
 `IErrorInfo` obiekt.  
  
## <a name="remarks"></a>Uwagi  
 `_com_raise_error`, który jest zdefiniowany w \<comdef.h >, może być zastąpiony napisany przez użytkownika wersję taką samą nazwę i prototypu. To było zrobić, jeśli chcesz używać `#import` , ale nie chcesz używać obsługę wyjątków C++. W takim przypadku użytkownik wersji `_com_raise_error` zdecydować, czy `longjmp` lub wyświetlić okno komunikatu i zatrzymany. Wersja użytkownika nie powinny zwracać, jednak, ponieważ kod obsługi kompilatora COM nie oczekuje do zwrócenia.  
  
 Można również użyć [_set_com_error_handler —](../cpp/set-com-error-handler.md) zastąpić domyślną funkcję obsługi błędów.  
  
 Domyślnie `_com_raise_error` jest zdefiniowana w następujący sposób:  
  
```cpp  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<comdef.h >  
  
 **Lib:** Jeśli **wchar_t jest typem natywnym** — opcja kompilatora jest włączona, użyj comsuppw.lib lub comsuppwd.lib. Jeśli **wchar_t jest typem natywnym** jest wyłączone, użyj comsupp.lib. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler](../cpp/set-com-error-handler.md)