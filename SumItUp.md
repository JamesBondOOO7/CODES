import java.util.*;

public class Main {
	public static ArrayList<ArrayList<Integer>> list = new ArrayList<>();
    public static void main(String args[]) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		ArrayList<Integer> arr = new ArrayList<>();
		for(int i = 0 ; i<n ; i++)
		{
			arr.add(sc.nextInt());
		}

		Collections.sort(arr);
		int target = sc.nextInt();
		ArrayList<Integer> helper = new ArrayList<>();
		SumItUp(arr , target , -1 , helper);
		
		for( ArrayList<Integer> val : list )
		{
			for( Integer ans : val)
			{
				System.out.print(ans + " ");
			}
			System.out.println();
		}
    }

	public static void SumItUp(ArrayList<Integer> arr , int target , int last_index , ArrayList<Integer> helper)
	{
		if( target == 0)
		{
			list.add(new ArrayList<>(helper));
			return;
		}
		if( target < 0)
		{
			return;
		}

		for(int i = last_index + 1 ; i<arr.size() ; i++)
		{
			helper.add(arr.get(i));
			SumItUp(arr , target - arr.get(i) , i , helper);
			helper.remove(helper.size() - 1);
		}
	}
}
