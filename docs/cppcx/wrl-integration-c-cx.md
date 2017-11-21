---
title: Integracja WRL (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 289c82a69ebc549d53e7b8ae49b6939200eb3aac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="wrl-integration-ccx"></a>Integracja WRL (C + +/ CX)
Za darmo można mieszać kodu za pomocą biblioteki WRL [!INCLUDE[cppwrl](includes/cppwrl-md.md)] ([!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]) kodu. W tej samej jednostce tłumaczenia, można użyć obiektów zadeklarowanych za pomocą biblioteki WRL uchwyt do obiektu (`^`) notacji i [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] wskaźnika inteligentnego (`ComPtr<T>`) notacji. Jednak ręcznie musi obsługiwać zwracanych wartości i [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] HRESULT wyjątki biblioteki WRL i kody błędów.  
  
## <a name="includecppwrlshortincludescppwrl-short-mdmd-development"></a>[!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]Programowanie  
 Aby uzyskać więcej informacji na temat tworzenia i używania [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] , zobacz [Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
### <a name="example"></a>Przykład  
 Poniższy fragment kodu przedstawia za pomocą biblioteki WRL i [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] użycie [!INCLUDE[wrt](includes/wrt-md.md)] klas i sprawdź, czy plik metadanych.  
>>>>>>> główne
  
 Przykład pobranych z fragment kodu w [forum aplikacje Sklepu Windows budynku](http://social.msdn.microsoft.com/Forums/winappswithnativecode/thread/211ef583-db11-4e55-926b-6d9ab53dbdb4). Autor następujący fragment kodu oferuje następujące zastrzeżenia i przekazanie:  
  
1.  C++ nie zapewnia poszczególnych interfejsów API w celu odzwierciedlenia w systemie [!INCLUDE[wrt](includes/wrt-md.md)] typów, ale pliki metadanych systemu Windows (.winmd) dla typu są w pełni zgodne z plikami metadanych CLR. System Windows udostępnia nowe metadane odnajdywania interfejsów API (RoGetMetaDataFile), aby uzyskać dostęp do pliku winmd dla danego typu. Jednak te interfejsy API są ograniczone użytkowania dla deweloperów języka C++, ponieważ nie można utworzyć wystąpienia klasy.  
  
2.  Jest skompilowany kod, należy również przekazać Runtimeobject.lib i Rometadata.lib do konsolidatora.  
  
3.  Ta Wstawka kodu jest przedstawiany jako — jest. Podczas gdy oczekiwano działał prawidłowo, prawdopodobnie może zawierać błędy.  
  
```  
  
#include <hstring.h>  
#include <cor.h>  
#include <rometadata.h>  
#include <rometadataresolution.h>  
#include <collection.h>  
  
namespace ABI_Isolation_Workaround {  
    #include <inspectable.h>  
    #include <WeakReference.h>  
}  
using namespace ABI_Isolation_Workaround;  
#include <wrl/client.h>  
  
using namespace Microsoft::WRL;  
using namespace Windows::Foundation::Collections;  
  
IVector<String^>^ GetTypeMethods(Object^);  
  
MainPage::MainPage()  
{  
    InitializeComponent();  
  
    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");  
    auto methods = GetTypeMethods(uri);  
  
    std::wstring strMethods;  
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {  
        strMethods += methodName->Data();  
        strMethods += L"\n";  
    });  
  
    wprintf_s(L"%s\n", strMethods.c_str());  
}  
  
IVector<String^>^ GetTypeMethods(Object^ instance)  
{  
    HRESULT hr;  
    HSTRING hStringClassName;  
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD  
    if (FAILED(hr))  
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD  
    String^ className = reinterpret_cast<String^>(hStringClassName);   
  
    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());  
    if (FAILED(hr))  
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD  
  
    HSTRING hStringFileName;  
    mdTypeDef typeDefToken;   
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);  
    if (FAILED(hr))  
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD  
    String^ fileName = reinterpret_cast<String^>(hStringFileName);  
  
    HCORENUM hCorEnum = 0;  
    mdMethodDef methodDefs[2048];  
    ULONG countMethodDefs = sizeof(methodDefs);  
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);  
    if (FAILED(hr))  
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD  
  
    wchar_t methodName[1024];  
    ULONG countMethodName;  
    std::wstring strMethods;  
    Vector<String^>^ retVal = ref new Vector<String^>();  
  
    for(int i = 0; i < countMethodDefs; ++i)  
    {  
        countMethodName = sizeof(methodName);  
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);  
        if (SUCCEEDED(hr))  
        {  
            methodName[ countMethodName ] = 0;  
            retVal->Append(ref new String(methodName));  
        }  
    }  
    return retVal;  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z innymi językami](interoperating-with-other-languages-c-cx.md)