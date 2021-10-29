# react-native-svg-test

 "yarn add react-native-svg" ile react-native-svg paketi yüklendi. Yerel dosyadaki bir svg dosyasını kullanmak için 
 "yarn add --dev react-native-svg-transformer" ile transformer paketi yüklendi.
 metro-config.js içerisine aşağıdaki kodu ekliyoruz.  
  
```
  const { getDefaultConfig } = require("metro-config");
  module.exports = (async () => {
  const {
    resolver: { sourceExts, assetExts }
  } = await getDefaultConfig();
  return {
    transformer: {
      babelTransformerPath: require.resolve("react-native-svg-transformer")
    },
    resolver: {
      assetExts: assetExts.filter(ext => ext !== "svg"),
      sourceExts: [...sourceExts, "svg"]
    }
  };
})(); 
```
Renklendirme işlemi için svg içerisindeki xml etikerlerinde yer alan fill kısmını kaldırıyoruz. Kaldırmamızdaki amaç varsayılan olarak bu renk ile görseli boyamasını engellemek.
Daha sonra kendimiz app.js içerisinde component gibi kullanarak boyayacağımız rengi gönderiyoruz.
