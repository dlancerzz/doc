# graphql-dotnet 分析及学习

1. 项目地址：

<https://github.com/graphql-dotnet/graphql-dotnet>

1. 获取源代码：

`git clone https://github.com/graphql-dotnet/graphql-dotnet.git`

1. 项目初始化及安装：(如果没有 nodejs 和 yarn 请先自行安装)

`yarn install`

`yarn start`

1. 对比安装前后目录：

![1](001.png)

项目目录下增加了 node_modules 是 nodejs 的包管理目录所有的公共包（库）都安装在这个目录下。

![2](002.png)

站点项目增加了public目录主要是生成界面的文件bundle.js

![3](003.png)

1. 我们分析一下启动项目GraphQL.GraphiQLCore

![4](004.png)

- Program.cs

`
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>()
                .UseWebRoot("public")
                .Build();
    }
`

简单的代码，指定启动目录为public，就是我们刚刚生成文件的目录。
