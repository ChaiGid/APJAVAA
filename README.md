package moreArrays;

	public class Rational 
	{
		private int myNumer = 0;
		private int myDenom = 1;
		public Rational()
		{
			myNumer = 0;
			myDenom = 1;
		}
		public Rational(int myNum, int myDen)
		{
			myNumer = myNum;
			myDenom = myDen;
		}
		public int getNum()
		{
			return myNumer;
		}
		public int getDen()
		{
			return myDenom;
		}
		public void setNum(int myNum)
		{
			myNumer = myNum;
		}
		public void setDen(int myDen)
		{
			myDenom = myDen;
		}
		public String toString(int numer, int denom)
		{
			return numer + "/" + denom;
		}
		public int compareTo(Rational other)
		{
			int newNumer = other.getNum();
			int newDenom = other.getDen();
			double diff1 = other.toDecimal(newNumer, newDenom);
			double diff2 = other.toDecimal(myNumer, myDenom);
			if(diff2 > diff1)
			{
				return (int) (diff2 - diff1);
			}
			else if(diff1 > diff2)
			{
				return (int) (diff1 - diff2);
			}
			else
			{
				int zero = 0;
				return zero;
			}
		}
		public double toDecimal() {
            double returnDouble = ((double) this.myNumer) / this.myDenom;
            return returnDouble;
		}
		public double toDecimal(int myNumer, int myDenom) {
            double returnDouble = ((double) this.myNumer) / this.myDenom;
            return returnDouble;
		}
		public Rational subtract(Rational rat)
			{
				Rational returnRat = new Rational(this.myNumer * rat.getDen() + rat.getNum() * this.myDenom, this.myDenom * rat.getDen());
	            return returnRat;
			}
		public Rational add(Rational rat) 
		{
			Rational returnRat = new Rational(this.myNumer * rat.getDen() + rat.getNum() * this.myDenom, this.myDenom * rat.getDen());
            return returnRat;
		}
		public boolean equals(Rational rat) {
			if (this.myNumer == rat.getNum() && this.myDenom == rat.getDen())
			{
				return true;
		
			}
			else
			{
				return false;
			}
            
    }
		
	}
package moreArrays;

import java.util.ArrayList;
public class FractionList 
{
	private ArrayList<Rational> values;
	public FractionList()
	{
		values = new ArrayList<Rational>();
	}
	public void addFraction(Rational value)
	{
		this.values.add(value);
	}
	public void removeFraction(int removalIndex)
	{
		this.values.remove(removalIndex);
	}
	public Rational sum()
	{
		Rational returnSum = new Rational();
		int size = this.values.size();
		for (int i = 0; i < size; i++)
		{
			returnSum = returnSum.add(this.values.get(i));
		}
		return returnSum;
	}
	public double getAverage()
	{
		double avgpt1 = this.sum().toDecimal();
		int avgpt2 = this.values.size();
		double returnAverage = avgpt1 / avgpt2;
		return returnAverage;
	}
	public Rational getMax()
	{
		int size = this.values.size();
		Rational max = new Rational();
		for(int i = 0; i < size; i++)
		{
			if(this.values.get(i).compareTo(max) > 0)
			{
				max = this.values.get(i);
			}
		}
		return max;
	}
	public Rational getMin()
	{
		int size = this.values.size();
		Rational min = new Rational();
		for(int i = 0; i > size; i++)
		{
			if(this.values.get(i).compareTo(min) > 0)
			{
				min = this.values.get(i);
			}
		}
		return min;
	}
	public int getMaxIndex()
	{
		int index=0;
		int size = this.values.size();
		Rational max = new Rational();
		for(int i = 0; i < size; i++)
		{
			if((this.values.get(i).compareTo(max) > 0))
			{
				max = this.values.get(i);
				index = i;
			}
		}
		return index;
	}
	public int getMinIndex()
	{
		int index=0;
		int size = this.values.size();
		Rational min = new Rational();
		for(int i = 0; i > size; i++)
		{
			if((this.values.get(i).compareTo(min) > 0))
			{
				min = this.values.get(i);
				index = i;
			}
		}
		return index;
	}
	public void removeLargest()
	{
		this.values.remove(this.getMaxIndex());
		
	}
	public void removeSmallest()
	{
		this.values.remove(this.getMinIndex());
	}
	
	}



