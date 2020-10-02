### 一、合约
一共分为TokenBank、ERC20、ERC721、Sensitive、BizMarket、UserToken 合约

- TokenBank：主要合约逻辑。其中实现了创建token以及合约的基本信息存储。
- ERC20、ERC721：两个token的标准合约
- Sensitive：敏感词合约
- BizMarket：营销合约，配置广告等业务逻辑
- UserToken：用户token合约。

### 二、接口文档

#### 1、查询top-token

合约名称： TokenBank

合约函数： getTopToken

入参： 无

出参： (address[] tokens)

示例： [0x18c7e9e088cd75f69c36331a6517271bcc502651,0x18c7e9e088cd75f69c36331a6517271bcc502651]

#### 2、查询首页token

合约名称： TokenBank

合约函数： getHomeTokenList

入参： (uint pageNo, uint pageSize)

出参： address[] 列表

示例： [0x18c7e9e088cd75f69c36331a6517271bcc502651,0x18c7e9e088cd75f69c36331a6517271bcc502651]

#### 3、查询合约信息

合约名称： TokenBank

合约函数： getTokenInfo

入参： (address _userAccount, address _token)

出参： (
    string tokenName,
    string shorthandName,
    address token,
    address owner,
    uint totalSupply,
    uint flowNum,
    uint holderNum,
    uint haveNum,
    uint collection, 
    string img,
    uint burning,
    uint increase,
    uint decimals,
    string note,
    uint tokenType
)

注释： 
> collection 0：未收藏，1：已收藏； 
> burning 0：不能燃烧，1：可以燃烧； 
> increase 0：不能增发，1：可以增发；
> tokenType 0：erc20，1：erc721

#### 4、根据简称搜索token

合约名称：TokenBank

合约函数： getTokenByShorthandName

入参：(string _shorthandName, address _userAccount)

出参：(
       string tokenName,
       string shorthandName,
       address token,
       address owner,
       uint totalSupply,
       uint flowNum,
       uint holderNum,
       uint haveNum,
       uint collection, 
       string img,
       uint burning,
       uint increase,
       uint decimals,
       string note,
       string attribute,
       uint tokenType
   )
   
#### 5、检查token是否可用

合约名称：TokenBank

合约函数：checkShorthandName

入参：(string _shorthandName)

出参：(bool result)

注释：true 可用，false 不可用

#### 6、发行token

合约名称：TokenBank

合约函数：publishToken

入参： (
    uint _tokenType,
    string _tokenName,
    string _shorthandName,
    uint _totalSupply,
    string _img,
    uint _burning,
    uint _increase,
    uint _decimals,
    string _note,
    string _attribute
)

出参： (
    string result
)

注释： 'success' 成功； 'sensitive' 敏感的简称； 'exists' 简称已存在；

#### 7、获取用户token列表

合约名称：UserToken

合约函数：getUserTokenList

入参：(uint _range, uint _option, address _userAccount, uint pageNo, uint pageSize)

出参： (address[] tokens)

注释： 
> range 1：全部；2：erc20；3：erc721 。 option 1：我的收藏；2：我的创建

#### 8、收藏token

合约名称：UserToken

合约函数：collectionToken

入参： (address _token, uint _option)

出参： (string result)

注释：
> _option 1：收藏； 2：取消收藏。 result 'success'：成功；'not exists'：token不存在。

#### 9、添加我的token(给TokenBank使用)

合约名称：UserToken

合约函数：addMyToken

入参：(address _token, address _userAccount)

出参：(bool result)

#### 10、查询banner

合约名称：BizMarket

合约函数：getBanner

入参：无

出参：(string bannerListStr)

注释：
> 出参格式是json字符串，由前端进行自行定义。

#### 11、设置banner

合约名称：BizMarket

合约函数：setBanner

入参：(string _bannerListStr)

出参：无

注释：
> 入参格式是json字符串，由前端进行自行定义。

#### 12、查询热门搜索

合约名称：BizMarket

合约函数：getHotSearch

入参：无

出参：(string hotSearchListStr)

注释：
> 出参格式是json字符串，由前端进行自行定义。

#### 13、设置热门搜索

合约名称：BizMarket

合约函数：setHotSearch

入参：(string _hotSearchListStr)

出参：无

注释：
> 入参格式是json字符串，由前端进行自行定义。

#### 14、添加敏感词

合约名称：Sensitive

合约函数：addWords

入参：(string _words)

出参：无

#### 15、移除token(给Sensitive合约使用)

合约名称：TokenBank

合约函数：removeToken

入参：(string _shorthandName)

出参：无

#### 16、判断是否敏感(给TokenBank合约使用)

合约名称：Sensitive

合约函数：checkWords

入参：(string _words)

出参：(bool result)

#### 17、ERC20转账

合约名称：ERC20

合约函数：transfer

入参：(address to, uint256 value)

出参：(bool result)

注释：
> 这里调用的是token的合约方法

#### 18、ERC721转账

合约名称：ERC721

合约函数：transferFrom

入参：(address from, address to, uint256 tokenId)

出参：无

注释：
> 这里调用的是token的合约方法

#### 19、燃烧Token

合约名称：Token

合约函数：burning

入参：(uint _num)

出参：无

注释：
> 这里调用的是token的合约方法

#### 20、增发Token

合约名称：Token

合约函数：increase

入参：(uint _num)

出参：无

注释：
> 这里调用的是token的合约方法