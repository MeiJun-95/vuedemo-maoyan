<template>
  <i class="iconfont" :style="iconStyle" v-html="name"></i>
  <!-- v-html会将元素当成HTML标签解析后输出 -->
</template>

<script>
export default {
  name: 'icon',
  props: {
    name: {
      type: String,
      require: true
    },
    iconStyle: {
      type: Object,
      default: {fontSize: '20px', color: '#696969'}
    }
  }
}
</script>

<style scoped>
@font-face {font-family: "iconfont";
  src: url('../assets/iconfont/iconfont.eot?t=1571727022407'); /* IE9 */
  src: url('../assets/iconfont/iconfont.eot?t=1571727022407#iefix') format('embedded-opentype'), /* IE6-IE8 */
  url('data:application/x-font-woff2;charset=utf-8;base64,d09GMgABAAAAAAWQAAsAAAAACsAAAAVBAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHEIGVgCDSAqILIcOATYCJAMYCw4ABCAFhG0HXRtJCREVpDuR/Syw26iDJCgEq6wcMuJJeW2eDfd9iIDa77d3T75gliCRTLon1US3iIeOVxolMXQNhVA8JNI//jtzXnYjHrE5UMkJUaVz6U3rpHVQCouC/LrFOQd4Ih11iXL25NG3XQaUD0iryydAQN7/HEu9zOdR366CtarXRXuj8SiBBhTRFi16I5rzFvFsugvFpAzA7QSUdYiGpjSVOhBIMUeAIXstTb1A4AlKY5hB0ZMjp6YQLoGrGGdyrgG4MH4//EFiEIAoS4AduthY0hfy37i92YmRHSR01RBgKi+O21kk6AFSwjmaPATMsvcYzjK2NW4aQLWiKC2rE35viDdJb3Z2dOCxsmxQzfuSCpJG/vMIOVBnNWBnWxmfblJEyqefiMAnISLhM0lE5HNnUAbevMTJbSCsAIRnwPYclcoEUVWKy6MjJIylCpYIvysECfVKUGzIofaI0jGGELt4kSdtNS7xNsr2HfPFWda41MfiHoooSoctPRkmX3/ci2NG5PkYxoCSF3vRtJ674sRQhglFIrSO0h2i9DQdtnGpO2Gn3ZzilDSr9idYjyDb4pD1rJFletsYA8u6OWk9RZlIm8WBkNlptYPeQdqY7sgp6zbQ4t7oMHs0bbmZdO3bz05uGnqUJerVNyW+ms5Q6qTd6kQt1DfCaD+JYXqvZbXn6aBVVPEFpm3fMfK49aT5hM6yxby1gPgm08G/3YL4jevBAF5DPHYDrZcVa613kjCMsQYH2+jetTZAd+s93AyG0enE5rReanWaHY0i+/qNHsYjLbYyXnt4+4oLseGxIDsIHAMkDFW7LeCoi1t93sFhxeo5zDXFNTS/urn9u/cU5bKcBU5Q7pZeTun8X+hy3TwQ/gMZUXpJ2Q6d1cUJLtP+vbp5ProG324N7t25aQfkQdfZjzekmTCtsKy77vlkD7Rbnah59Yy4dYt49ipJ43pa6TH5OXoZYRmuTTf5ey+oI0RlfG1D6Jo1UmfonB3qiJxvwkfVUWGLFqxcc3WugJi2QgCxrYJK2Fx5VAD3QZIZ+XmjPEepl57hofSYERkVGTnDUwmtw7fEG3lIN2iQjtgQ6OByeLxxW3Pw9O3YMNF1t0di7vitG8ZzuI7qrENFj10fi7Bh07a3XwvQ679/l+4Aox90jIIvGi4IHqNqVEeVw4PUsQrCwvNILVqrTTSpm4jGjAjCrvLa1djP/V5o2Ywxn6XbFZP27p2k2C79zOCbwVhmezlcBDXbGzUZteuhF77/76cfvkr84IF4FX7w09/9uKXfY44sGO4mzsoSD8HLwDgAVG6rB7A6gMp8rBYjAYhPnCcAJDucd7T9XF2FESf4bvrfa8w95Nm/BVUH/bIP6uIOo1iZj0P+VlEktel0NqWcl34tLJSn77mlMZUgdwTiekSZL+IkzjZ6Upa7JfVggqIWB6KCdkgUdSJTbA9kqoxArmgUyrppz67SZAhgQioEujinEpDN7ATFxB9UM9eRGvYx6DY+g2GWCgOflpcc2hYOzgWyCl3o3UOLoMwTkWpgDn2gXyescFsM7geLMqxAQmy8v+uOGRZlHDG08U/DKg8aC0pBQ+6GSUIwqKAIRbVrrqqvExfXiL3Rrg+l0sBZATEV5AK99UALgWQ8benKIND5B+SrJZgiZs6P8gcqlMKNgwSx4lMg784s1ZxtGT1Uw3cyjNY9oPE2mKSAhsZRwpsEDMJ3iiChstOco/7liKMLNaZ17up3p0t5HZI0wB5hxEEYwhEX8RAf7MPM72uWsZGn5oM6dL0pXhsPGa0lFy03NCQJSBIAAAA=') format('woff2'),
  url('../assets/iconfont/iconfont.woff?t=1571727022407') format('woff'),
  url('../assets/iconfont/iconfont.ttf?t=1571727022407') format('truetype'), /* chrome, firefox, opera, Safari, Android, iOS 4.2+ */
  url('../assets/iconfont/iconfont.svg?t=1571727022407#iconfont') format('svg'); /* iOS 4.1- */
}

.iconfont {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>