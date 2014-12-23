#include <stdio.h>
#define LeapYearDays 366
#define YearDays 365

typedef struct Date
{
	int m_year;
	int m_month;
	int m_days;
}Date;

int CountDays(Date dt);
void PrintfDate(Date dt,int Week_date);
int WeekDate(Date dt);

int main(int argc,char ** argv)
{
	Date dt1;
	printf("\t\t\tWeclome to my date.\n");
	while(1)
	{
		printf("Please intput date your want to look:(such as 1992/10/09)\n");
		int ret = scanf("%d/%d/%d",&dt1.m_year,&dt1.m_month,&dt1.m_days);
		char buf[48];
		if (ret != 3)
		{
			printf("Intput error.\n");
			gets(buf);
			continue;
		}
		if( dt1.m_month < 1 || dt1.m_days < 1)
			printf("Intput error\n");
	//1992/10/09为星期五，该年为闰年
		int Differ_days =  CountDays(dt1);
		int Week_date;
		int ret2 = WeekDate(dt1);
		if(ret2)	
			Week_date = (Differ_days % 7 ) < 3 ? (Differ_days % 7 + 5) : (Differ_days % 7 - 2);
		else
			Week_date = (Differ_days % 7 ) > -5 ? (Differ_days % 7 + 5) : Differ_days % 7 == -5 ? 7 : 6;

		
		printf("\n");
		printf("\n");
		printf("\n");
		
		PrintfDate(dt1,Week_date);
	}
}

int CountDays(Date dt)
{
	int days[2][12] = {{31,28,31,30,31,30,31,31,30,31,30,31},{31,29,31,30,31,30,31,31,30,31,30,31}};
	int Year_days = 0;
	if(dt.m_year == 1992)
	{
		int i = 1;
		int j;
		for(j = 0;j < dt.m_month - 1;j ++)
				Year_days += days[i][j];
		Year_days += 1;
		return Year_days - 283;
	}
	if(dt.m_year > 1992)
	{
		int i;
		if((dt.m_year - 1992) % 4)
			i =1;
		i = 0;
		int j;
		for(j = 0;j < dt.m_month - 1;j ++)
				Year_days += days[i][j];
		Year_days += 1;
		return  ((dt.m_year - 1992) % 4 == 0) ? (83 + YearDays * (dt.m_year - 1993) + (dt.m_year - 1992) / 4 - 1 + Year_days) : (83 + YearDays * (dt.m_year - 1993) + (dt.m_year - 1992) / 4 + Year_days);
	}
	if(dt.m_year < 1992)
	{
		int i;
		if((dt.m_year - 1992) % 4)
			i =1;
		i = 0;
		int j;
		for(j = 11;j > dt.m_month -1 ;j --)
			Year_days += -days[i][j];
		Year_days += 1 - days[i][dt.m_month -1];
		return  ((dt.m_year - 1992) % 4 == 0) ? (  YearDays * (dt.m_year - 1991) + (dt.m_year - 1992) / 4 + 1 + Year_days - 283) : ( YearDays * (dt.m_year - 1991) + (dt.m_year - 1992) / 4 + Year_days -283);
	}
	
}

void PrintfDate(Date dt,int Week_date)
{
	int days[2][12] = {{31,28,31,30,31,30,31,31,30,31,30,31},{31,29,31,30,31,30,31,31,30,31,30,31}};
	int date[6][7] = {0};
	int i;
	if((dt.m_year - 1992) % 4)
		i =1;
	i = 0;
	int j = 0;
	int tmp = days[i][dt.m_month - 1] + 1;
	for(i = 1; i < tmp ;i++)
	{
		if(Week_date != 7)
		{
			date[j][Week_date] = i;
			Week_date ++;	
			if (Week_date > 6)
			{
				j++;
				Week_date = 0;
			}
		}
		else
		{
			Week_date = 0;
			date[j][Week_date] = i;
			Week_date ++;	
		}
	}
	
	printf("\t\t\t%d/%02d/%02d\n",dt.m_year,dt.m_month,dt.m_days);
	printf("\t  Sun  Mon  Tue  Wed  Thu  Fri  Sat\n");
	for(i = 0;i < 6;i ++)
	{
		printf("\t");
		for(j = 0;j < 7; j ++)
		{
			if(date[i][j] == 0)
				printf("     ");
			else
			printf("  %02d ",date[i][j]);
		}   
		printf("\n");
	}
}

int WeekDate(Date dt1)
{
	if(dt1.m_year < 1992)
		return 0;
	if(dt1.m_year == 1992)
		if(dt1.m_month < 10)
			return 0;
		if(dt1.m_month == 10)
			if(dt1.m_days < 9 )
				return 0;
	return 1;
}
