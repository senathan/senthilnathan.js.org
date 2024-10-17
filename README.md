# senthilnathan.js.org

import org.springframework.data.jpa.repository.Query;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.repository.query.Param;
import org.springframework.stereotype.Repository;

@Repository
public interface YourEntityRepository extends JpaRepository<YourEntity, Long> {

    @Query("SELECT y FROM YourEntity y WHERE " +
           "(y.column1 LIKE %:searchText% OR y.column2 LIKE %:searchText% OR " +
           "y.column3 LIKE %:searchText% OR y.column4 LIKE %:searchText% OR " +
           "y.column5 LIKE %:searchText%) AND " +
           "y.dropdownColumn1 = :dropdownValue1 AND " +
           "y.dropdownColumn2 = :dropdownValue2 AND " +
           "y.dropdownColumn3 = :dropdownValue3 AND " +
           "((:failChecked = true AND (y.A = 'Failed' OR y.B = 'Failed' OR y.C = 'Failed')) OR " +
           "(:doneChecked = true AND (y.A = 'Done' OR y.B = 'Done' OR y.C = 'Done')) OR " +
           "(:notStartedChecked = true AND (y.A = 'Not_Started' OR y.B = 'Not_Started' OR y.C = 'Not_Started')) OR " +
           "(:inProgressChecked = true AND (y.A = 'In_Progress' OR y.B = 'In_Progress' OR y.C = 'In_Progress')))")
    List<YourEntity> findBySearchTextAndFilters(@Param("searchText") String searchText,
                                                @Param("dropdownValue1") String dropdownValue1,
                                                @Param("dropdownValue2") String dropdownValue2,
                                                @Param("dropdownValue3") String dropdownValue3,
                                                @Param("failChecked") Boolean failChecked,
                                                @Param("doneChecked") Boolean doneChecked,
                                                @Param("notStartedChecked") Boolean notStartedChecked,
                                                @Param("inProgressChecked") Boolean inProgressChecked);
}
