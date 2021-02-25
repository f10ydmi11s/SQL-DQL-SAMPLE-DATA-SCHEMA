# SQL-DQL-SAMPLE-DATA-SCHEMA
MS SQL script to create the tables and populate them with data.

USE [test]
GO
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[complaints](
	[complaintsID] [int] NOT NULL,
	[complaint] [nvarchar](50) NULL,
 CONSTRAINT [PK_complaints] PRIMARY KEY CLUSTERED 
(
	[complaintsID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[members]    Script Date: 2/25/2021 7:48:13 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[members](
	[memberID] [int] NOT NULL,
	[name] [nvarchar](50) NULL,
	[positionID] [int] NULL,
	[complaintsID] [int] NULL,
 CONSTRAINT [PK_members] PRIMARY KEY CLUSTERED 
(
	[memberID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[positions]    Script Date: 2/25/2021 7:48:13 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[positions](
	[positionID] [int] NOT NULL,
	[position] [nvarchar](50) NULL,
 CONSTRAINT [PK_positions] PRIMARY KEY CLUSTERED 
(
	[positionID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
INSERT [dbo].[complaints] ([complaintsID], [complaint]) VALUES (1, N'No response')
GO
INSERT [dbo].[complaints] ([complaintsID], [complaint]) VALUES (2, N'No return call')
GO
INSERT [dbo].[complaints] ([complaintsID], [complaint]) VALUES (3, N'Long wait')
GO
INSERT [dbo].[members] ([memberID], [name], [positionID], [complaintsID]) VALUES (1, N'Angel', 1, NULL)
GO
INSERT [dbo].[members] ([memberID], [name], [positionID], [complaintsID]) VALUES (2, N'Hess', 3, NULL)
GO
INSERT [dbo].[members] ([memberID], [name], [positionID], [complaintsID]) VALUES (3, N'Lawler', 2, NULL)
GO
INSERT [dbo].[members] ([memberID], [name], [positionID], [complaintsID]) VALUES (4, N'Hester', 1, NULL)
GO
INSERT [dbo].[members] ([memberID], [name], [positionID], [complaintsID]) VALUES (5, N'Brumfield', 5, NULL)
GO
INSERT [dbo].[members] ([memberID], [name], [positionID], [complaintsID]) VALUES (6, N'Rock', 8, 1)
GO
INSERT [dbo].[members] ([memberID], [name], [positionID], [complaintsID]) VALUES (7, N'Dehart', NULL, 1)
GO
INSERT [dbo].[members] ([memberID], [name], [positionID], [complaintsID]) VALUES (8, N'Bruner', NULL, 2)
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (1, N'Specialist')
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (2, N'President')
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (3, N'Business Consultant')
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (4, N'Developer')
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (5, N'Senior Specialist')
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (6, N'Assistant')
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (7, N'Board Member')
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (8, N'Senior Consultant')
GO
INSERT [dbo].[positions] ([positionID], [position]) VALUES (9, N'Senior Specialist')
GO
ALTER TABLE [dbo].[members]  WITH CHECK ADD  CONSTRAINT [FK_members_complaints] FOREIGN KEY([complaintsID])
REFERENCES [dbo].[complaints] ([complaintsID])
GO
ALTER TABLE [dbo].[members] CHECK CONSTRAINT [FK_members_complaints]
GO
ALTER TABLE [dbo].[members]  WITH CHECK ADD  CONSTRAINT [FK_members_positions] FOREIGN KEY([positionID])
REFERENCES [dbo].[positions] ([positionID])
GO
ALTER TABLE [dbo].[members] CHECK CONSTRAINT [FK_members_positions]
GO
