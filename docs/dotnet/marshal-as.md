---
title: marshal_as — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ebca4a94fa48feb4ff5fb897293303a395ac4eb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="marshalas"></a>marshal_as
Ta metoda konwertuje dane między środowiskach natywnych i zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `input`  
 Wartość, która ma być kierować do `To_Type` zmiennej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zmienna typu `To_Type` czyli przekonwertowanego wartość `input`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest uproszczony sposób konwertowania danych między typami natywnych i zarządzanych. Aby ustalić, jakie typy danych są obsługiwane, zobacz [omówienie z Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md). Konwersje niektórych danych wymaga kontekstu. Możesz przekształcić tych typów danych przy użyciu [marshal_context — klasa](../dotnet/marshal-context-class.md).  
  
 Jeśli spróbujesz kierować dwa typy danych, które nie są obsługiwane, `marshal_as` wygeneruje błąd [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) w czasie kompilacji. Przeczytaj wiadomość dostarczona dotyczącą tego błędu, aby uzyskać więcej informacji. `C4996` Błędu mogą być generowane dla więcej niż tylko przestarzałych funkcji. Przykładem jest próby skierowania dwa typy danych, które nie są obsługiwane.  
  
 Biblioteka organizowania składa się z kilku plików nagłówka. Wszelkie konwersja wymaga tylko jednego pliku, ale może zawierać dodatkowe pliki, jeśli zachodzi konieczność dla innych konwersji. Konwersje, które są skojarzone z pliki, które obejrzeć w tabeli w `Marshaling Overview`. Niezależnie od tego jaki konwersji chcesz zrobić, obszaru nazw wymagane jest zawsze efektu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie marshals z `const char*` do `System::String` typu zmiennej.  
  
```  
// marshal_as_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   const char* message = "Test String to Marshal";  
   String^ result;  
   result = marshal_as<String^>( message );  
   return 0;  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_context, klasa](../dotnet/marshal-context-class.md)