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
ms.openlocfilehash: 4e7b28c9d48704eede883cbcd387d9e77798647f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="comraiseerror"></a>_com_raise_error
**Microsoft Specific**  
  
 Zgłasza wyjątek [_com_error](../cpp/com-error-class.md) w odpowiedzi na awarię.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 `HRESULT` Informacje.  
  
 `perrinfo`  
 **IErrorInfo** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 `_com_raise_error`, która jest zdefiniowana w \<comdef.h >, może być zastąpiony zapisane przez użytkownika wersja tej samej nazwie i prototypu. Można to zrobić, jeśli chcesz użyć `#import` , ale nie chcesz używać C++, obsługa wyjątków. W takim przypadku użytkownik wersji **_com_raise_error —** zdecydować, czy `longjmp` lub wyświetlać okno komunikatu i zatrzymany. Wersja użytkownika nie może zwracać, jednak ponieważ kod obsługa kompilatora COM nie powinien zwrócić.  
  
 Można również użyć [_set_com_error_handler —](../cpp/set-com-error-handler.md) zastąpić domyślnej funkcji obsługi błędów.  
  
 Domyślnie `_com_raise_error` jest zdefiniowane w następujący sposób:  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<comdef.h >  
  
 **Lib:** Jeśli **wchar_t jest typem natywnym** kompilatora opcja jest włączona, należy użyć comsuppw.lib lub comsuppwd.lib. Jeśli **wchar_t jest typem natywnym** jest wyłączone, należy użyć comsupp.lib. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler](../cpp/set-com-error-handler.md)